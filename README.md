# lesson-master
## 事件循环

### 浏览器的进程模型

浏览器是一个<strong>多进程多线程</strong>的应用程序，为了避免相互影响，连环崩溃，启动浏览器后会自动开启多个进程，例如：

- 浏览器进程

​	主要负责页面展示、用户交互、子进程管理等。浏览器进程内部会开启多个线程处理不同的任务。

- 网络进程

​	负责网络资源的加载。网络进程内部会开启多个线程处理不同的任务

- 渲染进程

​	渲染进程启动后，会开启一个<strong>渲染主线程</strong>用于解析 HTML、CSS、JS 代码。默认情况下，浏览器会为每一个标签页开启一个新的渲染进程，避免相互影响。渲染主线程只有一个，也有其他的线程。

### 渲染主线程的工作模式（消息队列）

开始阶段，messageLoop 开启一个无线循环 for(;;)，每次循环会检查消息队列中是否有待执行的任务，若有，则取出下一个任务，若无，则进入休眠状态。其他线程包括渲染主线程均可向消息队列中添加任务，若在添加任务时渲染主线程处于休眠状态，则唤醒渲染主线程继续循环。整个过程即为事件循环。

### 异步

单线程时异步产生的原因，事件循环时异步的实现方式。

### 任务的优先级

任务没有优先级，任务有类型，任务队列有优先级。相同类型的任务必须放在一个任务队列中，不同类型的任务可以放在不同的任务队列中，其中微任务队列优先级最高。

## 浏览器渲染原理

