
### Selenium


Selenium 是一款开源且可移植的自动化软件测试工具，专门用于测试网页端应用程序或者采集网页端数据。它能够在不同的浏览器和操作系统上运行，具有很强的跨平台能力。Selenium可以帮助测试人员更高效地自动化测试基于Web网页端的应用程序，也可以帮忙开发者方便地完成网页端数据的采集工作。


### Chrome Dev Tools


Chrome Dev Tools 是直接内置于 Chrome 浏览器中的调试工具。它为开发人员提供了一整套用于检查、调试、分析和优化 Web 网页端应用程序的工具。下面举例讲述 Chrome Dev Tools 支持的一些功能：


#### 元素选项卡


元素选项卡可以显示当前页面的 DOM 树，使用者也可以通过该功能实时修改当前页面的 DOM 树。举例来讲，我们现在想修改百度搜索按钮背景颜色成红色，我们就可以通过元素选项卡来完成。我们在元素选项卡中选中搜索框的按钮并且将 background\-color 样式设置为红色即可，下方截图是实现的效果。


![](https://img2024.cnblogs.com/blog/714509/202412/714509-20241211191703687-604698951.png) ![](https://img2024.cnblogs.com/blog/714509/202412/714509-20241211191703663-569828269.png)


#### **控制台选项卡**


控制台选项卡类似于交互式的终端，我们可以在这里看到JavaScript代码打印的日志信息，方便我们定位问题，也可以在这里输入 JavaScript 代码，并且可以让这些代码实时生效，甚至改变原有网页的行为。例如，我们打开某个网站的登录页面并且在控制台选项卡中输入如下的代码：



```


|  | document.querySelector('button').addEventListener('click', function(){ |
| --- | --- |
|  | alert("login button is clicked"); |
|  | }); |


```

通过网页中注入上面的代码，我们可以监控到该页面上面所有 button 元素的点击操作，当用户点击登录按钮的时候就会弹窗显示消息“login button is clicked”。具体情形如下图所示：
![图片](https://img2024.cnblogs.com/blog/714509/202412/714509-20241211191704081-1525388753.png)


#### **源代码选项卡**


源代码选项卡可以查看完整的网页源代码，对源代码进行单步调试，观察代码的调用堆栈，也可以动态修改代码变量。为了能够更加清晰地说明源代码选项卡的作用，我简单编写了一个 HTML 页面。其内容如下所示：



```


|  |  |
| --- | --- |
|  |  |
|  |  |
|  |  |
|  | example page 1 |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |


```

首先，我们在 Chrome 浏览器中打开上面的网页内容，进入到开发者工具，切换到源代码选项卡，我们会看到下面的视图：
![图片](https://img2024.cnblogs.com/blog/714509/202412/714509-20241211191703637-166012291.png)
如上图所示，源代码选项卡主要由3个部分组成：


1. 文件导航窗口：文件导航窗口中列举了整个网页相关的文件列表和路径，主要包括：HTML，JavaScript，CSS 和浏览器扩展插件等。
2. 代码编辑窗口：源代码选项卡的第二个窗口是一个源代码编辑器，我们可以在这里查看和编辑各个文件的源代码，也可以在这里设置调试断点。
3. 调试信息窗口：调试信息窗口展示了当前设置的断点信息和调用堆栈信息等。


我们有两种方法可以给当前页面的代码设置断点。


**设置断点的第一种方法**是在代码编辑窗口中点击对应的行号设置断点。具体视图如下所示：


![图片](https://img2024.cnblogs.com/blog/714509/202412/714509-20241211191704055-844972334.png)
调试信息窗口中会展示我们设置的所有断点信息。除了设置普通的断点，我们还可以设置条件断点（Conditional Breakpoints）。现在，我们将上图中的第一个断点修改为条件断点，设置只有当 param 变量等于 World 的时候才会触发断点。设置后的效果如下图所示：


![图片](https://img2024.cnblogs.com/blog/714509/202412/714509-20241211191703669-1785876861.png)
**设置断点的第二种方式**是直接在代码编辑窗口中插入 debugger 命令。具体效果如下图所示：


![图片](https://img2024.cnblogs.com/blog/714509/202412/714509-20241211191704057-395431085.png)


#### **网络选项卡**


通过网络选项卡，我们可以观察到网络流量的情况以及网络的请求和响应。对于爬虫开发者来说，最感兴趣的内容应该是各个文件的具体请求和响应信息。通过网络选项卡，我们会看到浏览器实时发送和接收的每个请求。通过点击每个请求，我们可以可以访问请求和响应的具体信息，cookie 和耗时等。


![图片](https://img2024.cnblogs.com/blog/714509/202412/714509-20241211191703682-1642393825.png)


### Chrome DevTools Protocol (CDP)


Chrome DevTools Protocol（CDP）是一套用于与基于Chromium内核浏览器进行通信的 API。它允许开发者通过发送命令和接收事件来与浏览器进行交互，以实现自动化测试、性能分析、调试等功能。CDP 在自动化测试、前端开发和爬虫程序开发等很多领域都发挥着重要的作用。


Chrome 浏览器的开发者将 Chrome DevTools 的功能领域划分为大约50个，每个版本的浏览器支持的功能领域可能会有些许差异。具体的功能领域划分我们可以通过官方文档链接进行查询，[https://chromedevtools.github.io/devtools\-protocol/](https://github.com)。打开浏览器的开发者工具，我们可以开启实验特性下的协议监视器（protocol monitor）功能来查看当前浏览器页面发送的所有 CDP 指令。


### Selenium与CDP协议结合使用


在 Selenium 4 框架中，提供了两种与 Chrome Devtools 进行交互的方法，分别是 DevTools.send 方法和 ChromiumDriver.executeCdpCommand 方法。


DevTools 是 Selenium 框架为 CDP 协议编写的一个封装类，它内置了部分 CDP 协议指令。


ChromiumDriver 对象中的 executeCdpCommand 方法则是根据 CDP 协议指令的定义采用更加原始的方式直接向 Chrome 浏览器内核发送 CDP 协议指令。两种发送指令方式的差异性如下图所示：


![图片](https://img2024.cnblogs.com/blog/714509/202412/714509-20241211191703644-558308406.png)
接下来，我们分别采用DevTools.send方法和ChromiumDriver.sendCdpCommand方法来发送CDP协议指令来展示Selenium与CDP协议是如何结合在一起使用的。


#### 示例1：捕获网络请求数据和网络响应数据


首先，我们来看一看如何使用 DevTools 对象来操作 CDP 协议指令。假设，我们在进行数据采集的时候，希望能够实时记录某一个网站针对特定 URL 的请求数据和响应数据。这个时候，我们可以利用 CDP 协议中的 Network 领域功能来跟踪页面的相关网络活动。要实现捕获网络请求和响应数据的功能，我们首先需要使用 Network.enable 方法来开启页面的网络活动追踪功能，然后监听 Network.requestWillBeSent 事件和 Network.responseReceived 事件。具体代码示例如下所示：



```


|  | DevTools devTools = chromeDriver.getDevTools(); |
| --- | --- |
|  | devTools.createSession(); |
|  | devTools.send(Network.enable(Optional.empty(), Optional.empty(), Optional.empty())); |
|  | ThreadUtils.sleepQuietly(Duration.ofSeconds(5)); |
|  | devTools.addListener(Network.responseReceived(), response -> { |
|  | if(response.getResponse().getUrl().contains("token") || response.getResponse().getUrl().contains("userinfo")) { |
|  | String url = response.getResponse().getUrl(); |
|  | String responseBody = devTools.send(Network.getResponseBody(response.getRequestId())).getBody(); |
|  | System.out.println(String.format("request url & response body: %s, %s", url, responseBody)); |
|  | } |
|  | }); |
|  | chromeDriver.get("https://github.com/"); |


```

执行上述代码之后，我们会得到如下所示的打印结果。
![图片](https://img2024.cnblogs.com/blog/714509/202412/714509-20241211191703651-1598027079.png)


#### 示例2：打印网页内容


在第二个示例中，我们采用 executeCdpCommand 方法来直接发送 CDP 指令给浏览器内核。假设我们现在使用的是 v96 版本的 Chrome 浏览器，与该版本浏览器对应的 Selenium DevTools 包装类中并不支持 Page.printToPDF 的 CDP 协议指令，这样我们就不得不使用 executeCdpCommand 方法来直接发送 CDP 协议指令。


首先，我们打开链接：[https://chromedevtools.github.io/devtools\-protocol/tot/Page/\#method\-printToPDF](https://github.com):[FlowerCloud机场](https://hushicha.org)，查看具体的 Page.printToPDF 指令定义。


了解完指令定义之后，我们就可以按照指令定义来编写相关代码，具体代码示例如下所示：



```


|  | chromeDriver.get("https://github.com/"); |
| --- | --- |
|  | Thread.sleep(3000); |
|  | Map params = Maps.newHashMap(); |
|  | params.put("displayHeaderFooter", true); |
|  | params.put("paperWidth", 11.0f); |
|  | params.put("headerTemplate", "&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"); |
|  | Map response = chromeDriver.executeCdpCommand("Page.printToPDF", params); |
|  | Path destination = Paths.get("fullpage-screenshot-chrome.pdf"); |
|  | Files.write(destination, Base64.getDecoder().decode(response.get("data").toString())); |
|  | chromeDriver.quit(); |


```

上述代码执行之后，我们会得到一个 PDF 文件。


### 总结


本文介绍了有关 Chrome DevTools，Chrome DevTools Protocol 以及 Selenium 与 CDP 协议结合应用的一些基本知识。希望它可以您在编写自动化爬取/采集程序的时候帮助到您。


另外，更多有关网络数据采集\\爬取、验证码识别和逆向分析等相关知识，可以阅读我最近出版的《Java网络爬虫精解与实践》一书，该书知识结构紧凑，内容覆盖全面。


另外，该书还提供了对应的网络数据采集训练平台：[https://benshu.tech/crawler](https://github.com)。


