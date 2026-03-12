# 项目：待办事项应用

## 项目目标

本章我们将创建一个命令行待办事项（Todo List）应用，功能包括：
- 添加待办事项
- 查看所有待办事项
- 标记完成
- 删除待办事项
- 保存数据到文件

## 项目结构

```
todo-app/
├── src/
│   ├── main.claw    # 主程序
│   ├── storage.claw # 数据存储
│   └── todo.claw    # 待办事项处理
├── data/
│   └── todos.json   # 数据文件
└── config.json
```

## 代码实现

### 步骤 1：创建项目

```bash
claw new todo-app
cd todo-app
mkdir -p data
```

### 步骤 2：创建数据存储模块

创建 `src/storage.claw`：

```claw
import claw.fs
import claw.json

// 数据文件路径
DATA_FILE = "./data/todos.json"

// 加载数据
func loadData() {
    if fs.exists(DATA_FILE) {
        content = fs.readFile(DATA_FILE)
        if content != "" and content != null {
            return json.parse(content)
        }
    }
    return []
}

// 保存数据
func saveData(todos) {
    jsonStr = json.stringify(todos)
    fs.writeFile(DATA_FILE, jsonStr)
}

exports = {
    "loadData": loadData,
    "saveData": saveData
}
```

### 步骤 3：创建待办事项处理模块

创建 `src/todo.claw`：

```claw
// 添加待办事项
func addTodo(todos, title) {
    id = todos.length + 1
    newTodo = {
        "id": id,
        "title": title,
        "completed": false,
        "createdAt": date.now()
    }
    todos.push(newTodo)
    return todos
}

// 列出所有待办事项
func listTodos(todos) {
    if todos.length == 0 {
        print("暂无待办事项")
        return
    }

    print("")
    print("========== 待办事项列表 ==========")
    for todo in todos {
        status = todo.completed ? "[✓]" : "[ ]"
        print(status + " " + todo.id + ". " + todo.title)
    }
    print("==================================")
    print("共 " + todos.length + " 项")
}

// 标记完成
func completeTodo(todos, id) {
    found = false
    for todo in todos {
        if todo.id == id {
            todo.completed = true
            found = true
            print("已将 '" + todo.title + "' 标记为完成")
            break
        }
    }
    if not found {
        print("未找到 ID 为 " + id + " 的待办事项")
    }
    return todos
}

// 删除待办事项
func deleteTodo(todos, id) {
    newTodos = []
    found = false

    for todo in todos {
        if todo.id == id {
            found = true
            print("已删除：'" + todo.title + "'")
        } else {
            newTodos.push(todo)
        }
    }

    if not found {
        print("未找到 ID 为 " + id + " 的待办事项")
    }

    return newTodos
}

exports = {
    "addTodo": addTodo,
    "listTodos": listTodos,
    "completeTodo": completeTodo,
    "deleteTodo": deleteTodo
}
```

### 步骤 4：创建主程序

创建 `src/main.claw`：

```claw
import claw.io
import "./storage" as storage
import "./todo" as todo

// 加载数据
todos = storage.loadData()

print("=================================")
print("       欢迎使用待办事项！")
print("=================================")
print("")
print("命令说明：")
print("  add <事项>  - 添加待办事项")
print("  list       - 查看所有事项")
print("  done <ID>  - 标记完成")
print("  del <ID>   - 删除事项")
print("  help       - 显示帮助")
print("  quit       - 退出程序")
print("")

while true {
    print("")
    print("请输入命令：")
    input = io.input()

    if input == "quit" or input == "q" {
        storage.saveData(todos)
        print("数据已保存，再见！")
        break
    }

    if input == "help" or input == "h" {
        print("命令说明：")
        print("  add <事项>  - 添加待办事项")
        print("  list       - 查看所有事项")
        print("  done <ID>  - 标记完成")
        print("  del <ID>   - 删除事项")
        print("  help       - 显示帮助")
        print("  quit       - 退出程序")
        continue
    }

    parts = input.split(" ")
    command = parts[0]

    match command {
        "list", "ls", "l" => {
            todo.listTodos(todos)
        }

        "add", "a" => {
            if parts.length < 2 {
                print("用法：add <事项>")
                continue
            }
            // 合并剩余部分为标题
            title = parts.slice(1).join(" ")
            todos = todo.addTodo(todos, title)
            print("已添加：'" + title + "'")
        }

        "done", "complete", "c" => {
            if parts.length < 2 {
                print("用法：done <ID>")
                continue
            }
            id = parts[1].toNumber()
            if id == null {
                print("请输入有效的 ID")
                continue
            }
            todos = todo.completeTodo(todos, id)
        }

        "del", "delete", "d" => {
            if parts.length < 2 {
                print("用法：del <ID>")
                continue
            }
            id = parts[1].toNumber()
            if id == null {
                print("请输入有效的 ID")
                continue
            }
            todos = todo.deleteTodo(todos, id)
        }

        _ => {
            print("未知命令，输入 'help' 查看帮助")
        }
    }

    // 保存数据
    storage.saveData(todos)
}
```

### 步骤 5：运行程序

```bash
claw run src/main.claw
```

## 使用演示

```
=================================
       欢迎使用待办事项！
=================================

命令说明：
  add <事项>  - 添加待办事项
  list       - 查看所有事项
  done <ID>  - 标记完成
  del <ID>   - 删除事项
  help       - 显示帮助
  quit       - 退出程序

请输入命令：
> add 学习 OpenCLAW
已添加：'学习 OpenCLAW'

请输入命令：
> add 练习编程
已添加：'练习编程'

请输入命令：
> add 完成项目作业
已添加：'完成项目作业'

请输入命令：
> list

========== 待办事项列表 ==========
[ ] 1. 学习 OpenCLAW
[ ] 2. 练习编程
[ ] 3. 完成项目作业
==================================
共 3 项

请输入命令：
> done 1
已将 '学习 OpenCLAW' 标记为完成

请输入命令：
> list

========== 待办事项列表 ==========
[✓] 1. 学习 OpenCLAW
[ ] 2. 练习编程
[ ] 3. 完成项目作业
==================================
共 3 项

请输入命令：
> del 2
已删除：'练习编程'

请输入命令：
> list

========== 待办事项列表 ==========
[✓] 1. 学习 OpenCLAW
[ ] 3. 完成项目作业
==================================
共 2 项

请输入命令：
> quit
数据已保存，再见！
```

## 数据持久化

程序会自动保存数据到 `data/todos.json`：

```json
[
    {
        "id": 1,
        "title": "学习 OpenCLAW",
        "completed": true,
        "createdAt": 1700000000000
    },
    {
        "id": 3,
        "title": "完成项目作业",
        "completed": false,
        "createdAt": 1700000000001
    }
]
```

## 代码解释

### 1. 数据结构

每个待办事项是一个字典：

```claw
{
    "id": 1,
    "title": "学习 OpenCLAW",
    "completed": false,
    "createdAt": 1700000000000
}
```

### 2. 模块化设计

- `storage.claw`：负责数据的加载和保存
- `todo.claw`：负责待办事项的业务逻辑
- `main.claw`：负责用户交互

### 3. 数据持久化

使用 JSON 文件存储数据，程序退出时自动保存。

## 扩展练习

你可以尝试添加以下功能：

1. **编辑待办事项**：修改事项内容
2. **优先级**：添加优先级（高、中、低）
3. **分类标签**：添加分类功能
4. **截止日期**：添加提醒功能
5. **搜索**：按关键词搜索

### 扩展：添加优先级

修改待办事项结构：

```claw
func addTodo(todos, title, priority = "normal") {
    id = todos.length + 1
    newTodo = {
        "id": id,
        "title": title,
        "priority": priority,
        "completed": false
    }
    todos.push(newTodo)
    return todos
}
```

## 小结

本章我们完成了：
1. 创建待办事项应用
2. 实现添加、查看、完成、删除功能
3. 实现数据持久化（保存到文件）
4. 模块化代码结构

通过这个项目，我们学会了：
- 复杂业务逻辑的处理
- 数据结构和模块化编程
- 文件读写操作
- JSON 数据处理

## 恭喜完成教程！

你已经完成了 OpenCLAW 基础教程的所有章节！现在你：
- ✅ 了解 OpenCLAW 是什么
- ✅ 可以安装和配置开发环境
- ✅ 掌握基本语法和数据类型
- ✅ 会编写函数和模块
- ✅ 完成了一个计算器项目
- ✅ 完成了一个待办事项应用

接下来你可以：
- 继续学习更高级的主题
- 参与 OpenCLAW 开源项目
- 开发自己的应用

祝你编程愉快！

---

**上一章**：[项目：计算器](./chapter5-calculator.md)
