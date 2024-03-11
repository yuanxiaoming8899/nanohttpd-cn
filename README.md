<div class="Box-sc-g0xbh4-0 bJMeLZ js-snippet-clipboard-copy-unpositioned" data-hpc="true"><article class="markdown-body entry-content container-lg" itemprop="text"><div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">NanoHTTPD – Java 中的小型 Web 服务器</font></font></h2><a id="user-content-nanohttpd--a-tiny-web-server-in-java" class="anchor" aria-label="永久链接：NanoHTTPD – Java 中的小型 Web 服务器" href="#nanohttpd--a-tiny-web-server-in-java"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">NanoHTTPD</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是一个轻量级 HTTP 服务器，设计用于嵌入其他应用程序，根据修改的 BSD 许可证发布。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它正在 Github 上开发，并使用 Apache Maven 进行构建和单元测试：</font></font></p>
<ul dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">构建状态：</font></font><a href="https://travis-ci.org/NanoHttpd/nanohttpd" rel="nofollow"><img src="https://camo.githubusercontent.com/2e9c83c7f8fd8d666b3271aba4bb2311c43607d1dae46b9a6e8e9a28273ad154/68747470733a2f2f6170692e7472617669732d63692e6f72672f4e616e6f48747470642f6e616e6f68747470642e706e67" alt="构建状态" data-canonical-src="https://api.travis-ci.org/NanoHttpd/nanohttpd.png" style="max-width: 100%;"></a></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">覆盖状态：</font></font><a href="https://coveralls.io/r/NanoHttpd/nanohttpd" rel="nofollow"><img src="https://camo.githubusercontent.com/894de263342d3f36723a370fd71c2facf5b450c15f12c97a721d4f41c2997b34/68747470733a2f2f636f766572616c6c732e696f2f7265706f732f4e616e6f48747470642f6e616e6f68747470642f62616467652e737667" alt="覆盖状态" data-canonical-src="https://coveralls.io/repos/NanoHttpd/nanohttpd/badge.svg" style="max-width: 100%;"></a></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当前中央发布版本：</font></font><a href="https://maven-badges.herokuapp.com/maven-central/org.nanohttpd/nanohttpd" rel="nofollow"><img src="https://camo.githubusercontent.com/44f4f9f03a7f8bb7f04732a919c78e2ffede5a6364f2b65f473b15ab38fb1af4/68747470733a2f2f6d6176656e2d6261646765732e6865726f6b756170702e636f6d2f6d6176656e2d63656e7472616c2f6f72672e6e616e6f68747470642f6e616e6f68747470642f62616467652e737667" alt="梅文中心" data-canonical-src="https://maven-badges.herokuapp.com/maven-central/org.nanohttpd/nanohttpd/badge.svg" style="max-width: 100%;"></a></li>
</ul>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">快速开始</font></font></h2><a id="user-content-quickstart" class="anchor" aria-label="永久链接：快速入门" href="#quickstart"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们将使用 Maven 为构建/部署系统创建一个自定义 HTTP 服务器项目。</font><font style="vertical-align: inherit;">本教程假设您使用的是 Unix 变体和 shell。</font><font style="vertical-align: inherit;">首先，安装 Maven 和 Java SDK（如果尚未安装）。</font><font style="vertical-align: inherit;">然后运行：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>mvn compile
mvn exec:java -pl webserver -Dexec.mainClass="org.nanohttpd.webserver.SimpleWebServer"
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="mvn compile
mvn exec:java -pl webserver -Dexec.mainClass=&quot;org.nanohttpd.webserver.SimpleWebServer&quot;" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您现在应该有一个在</font></font><a href="http://localhost:8080/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://localhost:8080/</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上运行的 HTTP 文件服务器。</font></font></p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自定义网络应用程序</font></font></h3><a id="user-content-custom-web-app" class="anchor" aria-label="永久链接：自定义网络应用程序" href="#custom-web-app"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">接下来让我们提高标准并构建一个自定义 Web 应用程序：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>mvn archetype:generate -DgroupId=com.example -DartifactId=myHellopApp -DinteractiveMode=false
cd myHellopApp
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="mvn archetype:generate -DgroupId=com.example -DartifactId=myHellopApp -DinteractiveMode=false
cd myHellopApp" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑</font></font><code>pom.xml</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，并将其添加到 &lt;dependency&gt; 之间：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>&lt;dependency&gt;
	&lt;groupId&gt;org.nanohttpd&lt;/groupId&gt; &lt;!-- &lt;groupId&gt;com.nanohttpd&lt;/groupId&gt; for 2.1.0 and earlier --&gt;
	&lt;artifactId&gt;nanohttpd&lt;/artifactId&gt;
	&lt;version&gt;2.2.0&lt;/version&gt;
&lt;/dependency&gt;
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<dependency>
	<groupId>org.nanohttpd</groupId> <!-- <groupId>com.nanohttpd</groupId> for 2.1.0 and earlier -->
	<artifactId>nanohttpd</artifactId>
	<version>2.2.0</version>
</dependency>" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑</font></font><code>src/main/java/com/example/App.java</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并将其替换为：</font></font></p>
<div class="highlight highlight-source-java notranslate position-relative overflow-auto" dir="auto"><pre>    <span class="pl-k">package</span> <span class="pl-s1">com</span>.<span class="pl-s1">example</span>;
    
    <span class="pl-k">import</span> <span class="pl-s1">java</span>.<span class="pl-s1">io</span>.<span class="pl-s1">IOException</span>;
    <span class="pl-k">import</span> <span class="pl-s1">java</span>.<span class="pl-s1">util</span>.<span class="pl-s1">Map</span>;
    
    <span class="pl-k">import</span> <span class="pl-s1">fi</span>.<span class="pl-s1">iki</span>.<span class="pl-s1">elonen</span>.<span class="pl-s1">NanoHTTPD</span>;
    <span class="pl-c">// NOTE: If you're using NanoHTTPD &gt;= 3.0.0 the namespace is different,</span>
    <span class="pl-c">//       instead of the above import use the following:</span>
	<span class="pl-c">// import org.nanohttpd.NanoHTTPD;</span>
    
    <span class="pl-k">public</span> <span class="pl-k">class</span> <span class="pl-smi">App</span> <span class="pl-k">extends</span> <span class="pl-smi">NanoHTTPD</span> {
    
        <span class="pl-k">public</span> <span class="pl-smi">App</span>() <span class="pl-k">throws</span> <span class="pl-smi">IOException</span> {
            <span class="pl-en">super</span>(<span class="pl-c1">8080</span>);
            <span class="pl-en">start</span>(<span class="pl-smi">NanoHTTPD</span>.<span class="pl-c1">SOCKET_READ_TIMEOUT</span>, <span class="pl-c1">false</span>);
            <span class="pl-smi">System</span>.<span class="pl-s1">out</span>.<span class="pl-en">println</span>(<span class="pl-s">"<span class="pl-s">\n</span>Running! Point your browsers to http://localhost:8080/ <span class="pl-s">\n</span>"</span>);
        }
    
        <span class="pl-k">public</span> <span class="pl-k">static</span> <span class="pl-smi">void</span> <span class="pl-en">main</span>(<span class="pl-smi">String</span>[] <span class="pl-s1">args</span>) {
            <span class="pl-k">try</span> {
                <span class="pl-k">new</span> <span class="pl-smi">App</span>();
            } <span class="pl-k">catch</span> (<span class="pl-smi">IOException</span> <span class="pl-s1">ioe</span>) {
                <span class="pl-smi">System</span>.<span class="pl-s1">err</span>.<span class="pl-en">println</span>(<span class="pl-s">"Couldn't start server:<span class="pl-s">\n</span>"</span> + <span class="pl-s1">ioe</span>);
            }
        }
    
        <span class="pl-c1">@</span><span class="pl-c1">Override</span>
        <span class="pl-k">public</span> <span class="pl-smi">Response</span> <span class="pl-en">serve</span>(<span class="pl-smi">IHTTPSession</span> <span class="pl-s1">session</span>) {
            <span class="pl-smi">String</span> <span class="pl-s1">msg</span> = <span class="pl-s">"&lt;html&gt;&lt;body&gt;&lt;h1&gt;Hello server&lt;/h1&gt;<span class="pl-s">\n</span>"</span>;
            <span class="pl-smi">Map</span>&lt;<span class="pl-smi">String</span>, <span class="pl-smi">String</span>&gt; <span class="pl-s1">parms</span> = <span class="pl-s1">session</span>.<span class="pl-en">getParms</span>();
            <span class="pl-k">if</span> (<span class="pl-s1">parms</span>.<span class="pl-en">get</span>(<span class="pl-s">"username"</span>) == <span class="pl-c1">null</span>) {
                <span class="pl-s1">msg</span> += <span class="pl-s">"&lt;form action='?' method='get'&gt;<span class="pl-s">\n</span>  &lt;p&gt;Your name: &lt;input type='text' name='username'&gt;&lt;/p&gt;<span class="pl-s">\n</span>"</span> + <span class="pl-s">"&lt;/form&gt;<span class="pl-s">\n</span>"</span>;
            } <span class="pl-k">else</span> {
                <span class="pl-s1">msg</span> += <span class="pl-s">"&lt;p&gt;Hello, "</span> + <span class="pl-s1">parms</span>.<span class="pl-en">get</span>(<span class="pl-s">"username"</span>) + <span class="pl-s">"!&lt;/p&gt;"</span>;
            }
            <span class="pl-k">return</span> <span class="pl-en">newFixedLengthResponse</span>(<span class="pl-s1">msg</span> + <span class="pl-s">"&lt;/body&gt;&lt;/html&gt;<span class="pl-s">\n</span>"</span>);
        }
    }</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="    package com.example;
    
    import java.io.IOException;
    import java.util.Map;
    
    import fi.iki.elonen.NanoHTTPD;
    // NOTE: If you're using NanoHTTPD >= 3.0.0 the namespace is different,
    //       instead of the above import use the following:
	// import org.nanohttpd.NanoHTTPD;
    
    public class App extends NanoHTTPD {
    
        public App() throws IOException {
            super(8080);
            start(NanoHTTPD.SOCKET_READ_TIMEOUT, false);
            System.out.println(&quot;\nRunning! Point your browsers to http://localhost:8080/ \n&quot;);
        }
    
        public static void main(String[] args) {
            try {
                new App();
            } catch (IOException ioe) {
                System.err.println(&quot;Couldn't start server:\n&quot; + ioe);
            }
        }
    
        @Override
        public Response serve(IHTTPSession session) {
            String msg = &quot;<html><body><h1>Hello server</h1>\n&quot;;
            Map<String, String> parms = session.getParms();
            if (parms.get(&quot;username&quot;) == null) {
                msg += &quot;<form action='?' method='get'>\n  <p>Your name: <input type='text' name='username'></p>\n&quot; + &quot;</form>\n&quot;;
            } else {
                msg += &quot;<p>Hello, &quot; + parms.get(&quot;username&quot;) + &quot;!</p>&quot;;
            }
            return newFixedLengthResponse(msg + &quot;</body></html>\n&quot;);
        }
    }" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编译并运行服务器：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>mvn compile
mvn exec:java -Dexec.mainClass="com.example.App"
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="mvn compile
mvn exec:java -Dexec.mainClass=&quot;com.example.App&quot;" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果开始正常，请将浏览器指向</font></font><a href="http://localhost:8080/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://localhost:8080/</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并享受网络服务器，它会询问您的姓名并回复问候语。</font></font></p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">纳米粒子</font></font></h3><a id="user-content-nanolets" class="anchor" aria-label="永久链接：纳米粒子" href="#nanolets"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Nanolet 与 servlet 类似，只是它们的配置非常低。</font><font style="vertical-align: inherit;">它们为更复杂的服务器应用程序提供了易于使用的系统。</font><font style="vertical-align: inherit;">这篇文章必须用一个例子来扩展，所以现在看看单元测试的用法。</font></font><a href="https://github.com/NanoHttpd/nanohttpd/blob/master/nanolets/src/test/java/org/nanohttpd/junit/router/AppNanolets.java"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/NanoHttpd/nanohttpd/blob/master/nanolets/src/test/java/org/nanohttpd/junit/router/AppNanolets.java</font></font></a></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">地位</font></font></h2><a id="user-content-status" class="anchor" aria-label="永久链接：状态" href="#status"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们目前正在根据过去几个月集成的许多拉取请求和功能请求来稳定 NanoHTTPD。</font><font style="vertical-align: inherit;">下一个版本即将发布，并且在下一个版本之前不会再有任何“预期”的重大更改。</font><font style="vertical-align: inherit;">如果您想使用前沿版本，可以从 Github 克隆它，或者从 sonatype.org 获取它（请参阅下面的“Maven 依赖项/生活在边缘”）。</font></font></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目结构</font></font></h2><a id="user-content-project-structure" class="anchor" aria-label="永久链接：项目结构" href="#project-structure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">NanoHTTPD项目目前由四个部分组成：</font></font></p>
<ul dir="auto">
<li>
<p dir="auto"><code>/core</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">– 功能齐全的 HTTP(s) 服务器，由一 (1) 个 Java 文件组成，可以为您自己的项目进行定制/继承。</font></font></p>
</li>
<li>
<p dir="auto"><code>/samples</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">– 有关如何自定义 NanoHTTPD 的简单示例。</font><font style="vertical-align: inherit;">请参阅</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">HelloServer.java，</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">了解热情欢迎您的杀手级应用程序！</font></font></p>
</li>
<li>
<p dir="auto"><code>/websocket</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">– Websocket 实现，也在单个 Java 文件中。</font><font style="vertical-align: inherit;">取决于核心。</font></font></p>
</li>
<li>
<p dir="auto"><code>/webserver</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">– 独立文件服务器。</font><font style="vertical-align: inherit;">奔跑并享受。</font><font style="vertical-align: inherit;">一种流行的用途似乎是从 Android 设备上提供文件。</font></font></p>
</li>
<li>
<p dir="auto"><code>/nanolets</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">– 独立的 Nano 应用服务器，为实施者提供类似 servlet 的系统。</font></font></p>
</li>
<li>
<p dir="auto"><code>/fileupload</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">– 集成apache通用文件上传库。</font></font></p>
</li>
</ul>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">特征</font></font></h2><a id="user-content-features" class="anchor" aria-label="永久链接：特点" href="#features"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">核</font></font></h3><a id="user-content-core" class="anchor" aria-label="永久链接：核心" href="#core"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ul dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只有一个Java文件，提供HTTP 1.1支持。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有固定的配置文件、日志记录、授权等。（如果需要，请自行实现。不过，错误会传递给 java.util.logging。）</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">支持 HTTPS (SSL)。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对 cookie 的基本支持。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">支持GET和POST方法的参数解析。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对 HEAD、POST 和 DELETE 请求的一些内置支持。</font><font style="vertical-align: inherit;">不过，您可以轻松实现/自定义任何 HTTP 方法。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">支持文件上传。</font><font style="vertical-align: inherit;">对于小型上传使用内存，对于大型上传使用临时文件。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从不缓存任何东西。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">默认情况下不限制带宽、请求时间或同时连接。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所有标头名称都转换为小写，因此它们在浏览器/客户端之间不会有所不同。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">持久连接（连接“保持活动”）支持允许通过单个套接字连接提供多个请求。</font></font></li>
</ul>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">网络套接字</font></font></h3><a id="user-content-websocket" class="anchor" aria-label="永久链接：Websocket" href="#websocket"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ul dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在 Firefox、Chrome 和 IE 上进行了测试。</font></font></li>
</ul>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">网络服务器</font></font></h3><a id="user-content-webserver" class="anchor" aria-label="永久链接：网络服务器" href="#webserver"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ul dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">默认代码提供文件并显示（在控制台上打印）所有 HTTP 参数和标头。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">支持动态内容和文件服务。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件服务器支持目录列表</font></font><code>index.html</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>index.htm</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">.</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件服务器支持部分内容（流式传输和继续下载）。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件服务器支持 ETag。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件服务器对没有</font></font><code>/</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">.</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件服务器还可以提供很长的文件，而无需内存开销。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">包含最常见 MIME 类型的内置列表。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行时扩展支持（服务特定 MIME 类型的扩展）- 服务 Markdown 格式文件的示例扩展。</font><font style="vertical-align: inherit;">只需在 Web 服务器类路径中包含扩展 JAR 就足以加载扩展。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过参数
实现</font><font style="vertical-align: inherit;">简单的</font></font><a href="https://en.wikipedia.org/wiki/Cross-origin_resource_sharing" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">CORS</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">支持</font></font><code>--cors</code><font style="vertical-align: inherit;"></font><ul dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">默认情况下服务</font></font><code>Access-Control-Allow-Headers: origin,accept,content-type</code></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过设置系统属性来设置的可能性</font></font><code>Access-Control-Allow-Headers</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font><code>AccessControlAllowHeader</code></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">_例子： _</font></font><code>-DAccessControlAllowHeader=origin,accept,content-type,Authorization</code></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可能的值：
</font></font><ul dir="auto">
<li><code>--cors</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：激活 CORS 支持，</font></font><code>Access-Control-Allow-Origin</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将设置为</font></font><code>*</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></li>
<li><code>--cors=some_value</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">:</font></font><code>Access-Control-Allow-Origin</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将被设置为</font></font><code>some_value</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">.</font></font></li>
</ul>
</li>
</ul>
</li>
</ul>
<p dir="auto"><strong><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">CORS 参数示例</font></font></em></strong></p>
<ul dir="auto">
<li><code>--cors=http://appOne.company.com</code></li>
<li><code>--cors="http://appOne.company.com, http://appTwo.company.com"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">: 请注意双引号，以便两个 URL 被视为单个参数的一部分。</font></font></li>
</ul>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Maven 依赖项</font></font></h2><a id="user-content-maven-dependencies" class="anchor" aria-label="永久链接：Maven 依赖项" href="#maven-dependencies"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">NanoHTTPD是一个基于Maven的项目并部署到中央。</font><font style="vertical-align: inherit;">大多数开发环境都有访问中央存储库的方法。</font><font style="vertical-align: inherit;">Maven 中使用的坐标是：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>&lt;dependencies&gt;
	&lt;dependency&gt;
		&lt;groupId&gt;org.nanohttpd&lt;/groupId&gt; &lt;!-- &lt;groupId&gt;com.nanohttpd&lt;/groupId&gt; for 2.1.0 and earlier --&gt;
		&lt;artifactId&gt;nanohttpd&lt;/artifactId&gt;
		&lt;version&gt;CURRENT_VERSION&lt;/version&gt;
	&lt;/dependency&gt;
&lt;/dependencies&gt;
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<dependencies>
	<dependency>
		<groupId>org.nanohttpd</groupId> <!-- <groupId>com.nanohttpd</groupId> for 2.1.0 and earlier -->
		<artifactId>nanohttpd</artifactId>
		<version>CURRENT_VERSION</version>
	</dependency>
</dependencies>" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（替换为</font><a href="http://nanohttpd.org/" rel="nofollow"><font style="vertical-align: inherit;">http://nanohttpd.org/</font></a></font><code>CURRENT_VERSION</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上最新报告的内容</font><font style="vertical-align: inherit;">。）</font></font><a href="http://nanohttpd.org/" rel="nofollow"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您的开发环境的坐标应与这些相对应。</font><font style="vertical-align: inherit;">寻找旧版本时请务必小心，因为我们</font><font style="vertical-align: inherit;">在 2015 年中期将 groupId 从</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">com.nanohttpd</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">切换为</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">org.nanohttpd 。</font></font></em><font style="vertical-align: inherit;"></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">接下来取决于你使用 NanoHTTPD 的用途，主要有以下三种用途。</font></font></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Gradle 依赖项</font></font></h2><a id="user-content-gradle-dependencies" class="anchor" aria-label="永久链接：Gradle 依赖项" href="#gradle-dependencies"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在 gradle 中，您可以以相同的方式使用 NanoHTTPD，因为 gradle 访问相同的中央存储库：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dependencies {
	runtime(
		[group: 'org.nanohttpd', name: 'nanohttpd', version: 'CURRENT_VERSION'],
	)
}
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dependencies {
	runtime(
		[group: 'org.nanohttpd', name: 'nanohttpd', version: 'CURRENT_VERSION'],
	)
}" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（替换为</font><a href="http://nanohttpd.org/" rel="nofollow"><font style="vertical-align: inherit;">http://nanohttpd.org/</font></a></font><code>CURRENT_VERSION</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上最新报告的内容</font><font style="vertical-align: inherit;">。）</font></font><a href="http://nanohttpd.org/" rel="nofollow"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只需将名称替换为您要使用的模块的工件 ID，gradle 就会为您找到它。</font></font></p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开发您自己的专用 HTTP 服务</font></font></h3><a id="user-content-develop-your-own-specialized-http-service" class="anchor" aria-label="永久链接：开发您自己的专用 HTTP 服务" href="#develop-your-own-specialized-http-service"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于专门的 HTTP (HTTPS) 服务，您可以使用带有artifactId nanohttpd 的</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模块</font><font style="vertical-align: inherit;">。</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>	&lt;dependency&gt;
		&lt;groupId&gt;org.nanohttpd&lt;/groupId&gt; &lt;!-- &lt;groupId&gt;com.nanohttpd&lt;/groupId&gt; for 2.1.0 and earlier --&gt;
		&lt;artifactId&gt;nanohttpd&lt;/artifactId&gt;
		&lt;version&gt;CURRENT_VERSION&lt;/version&gt;
	&lt;/dependency&gt;
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="	<dependency>
		<groupId>org.nanohttpd</groupId> <!-- <groupId>com.nanohttpd</groupId> for 2.1.0 and earlier -->
		<artifactId>nanohttpd</artifactId>
		<version>CURRENT_VERSION</version>
	</dependency>" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这里，您编写自己的</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">org.nanohttpd.NanoHTTPD</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">子类来配置和服务请求。</font></font></p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开发基于 websocket 的服务</font></font></h3><a id="user-content-develop-a-websocket-based-service" class="anchor" aria-label="永久链接：开发基于 websocket 的服务" href="#develop-a-websocket-based-service"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于专门的 websocket 服务，您可以使用带有artifactId nanohttpd-websocket 的</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模块</font><font style="vertical-align: inherit;">。</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>	&lt;dependency&gt;
		&lt;groupId&gt;org.nanohttpd&lt;/groupId&gt; &lt;!-- &lt;groupId&gt;com.nanohttpd&lt;/groupId&gt; for 2.1.0 and earlier --&gt;
		&lt;artifactId&gt;nanohttpd-websocket&lt;/artifactId&gt;
		&lt;version&gt;CURRENT_VERSION&lt;/version&gt;
	&lt;/dependency&gt;
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="	<dependency>
		<groupId>org.nanohttpd</groupId> <!-- <groupId>com.nanohttpd</groupId> for 2.1.0 and earlier -->
		<artifactId>nanohttpd-websocket</artifactId>
		<version>CURRENT_VERSION</version>
	</dependency>" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这里，您编写自己的</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">org.nanohttpd.NanoWebSocketServer</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">子类来配置和服务 websocket 请求。</font><font style="vertical-align: inherit;">一个小的标准 echo 示例包含在</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">org.nanohttpd.samples.echo.DebugWebSocketServer</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中。</font><font style="vertical-align: inherit;">您可以使用它作为实现您自己的服务的起点。</font></font></p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开发自定义 HTTP 文件服务器</font></font></h3><a id="user-content-develop-a-custom-http-file-server" class="anchor" aria-label="永久链接：开发自定义 HTTP 文件服务器" href="#develop-a-custom-http-file-server"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于更经典的方法，也许只是创建一个 HTTP 服务器，主要为磁盘中的服务文件提供服务，您可以使用带有artifactId nanohttpd-webserver</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的模块</font><font style="vertical-align: inherit;">。</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>	&lt;dependency&gt;
		&lt;groupId&gt;org.nanohttpd&lt;/groupId&gt;
		&lt;artifactId&gt;nanohttpd-webserver&lt;/artifactId&gt;
		&lt;version&gt;CURRENT_VERSION&lt;/version&gt;
	&lt;/dependency&gt;
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="	<dependency>
		<groupId>org.nanohttpd</groupId>
		<artifactId>nanohttpd-webserver</artifactId>
		<version>CURRENT_VERSION</version>
	</dependency>" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">包含的类</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">org.nanohttpd.SimpleWebServer</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">旨在用作您自己的实现的起点，但它也可以按原样使用。</font><font style="vertical-align: inherit;">按原样启动类将在端口 8080 上启动 HTTP 服务器并发布当前目录。</font></font></p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生活在边缘</font></font></h3><a id="user-content-living-on-the-edge" class="anchor" aria-label="永久链接： 生活在边缘" href="#living-on-the-edge"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最新的 Github 主版本可以通过 sonatype.org 获取：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>&lt;dependencies&gt;
	&lt;dependency&gt;
		&lt;artifactId&gt;nanohttpd&lt;/artifactId&gt;
		&lt;groupId&gt;org.nanohttpd&lt;/groupId&gt;
		&lt;version&gt;XXXXX-SNAPSHOT&lt;/version&gt;
	&lt;/dependency&gt;
&lt;/dependencies&gt;
...
&lt;repositories&gt;
	&lt;repository&gt;
		&lt;id&gt;sonatype-snapshots&lt;/id&gt;
		&lt;url&gt;https://oss.sonatype.org/content/repositories/snapshots&lt;/url&gt;
		&lt;snapshots&gt;
			&lt;enabled&gt;true&lt;/enabled&gt;
		&lt;/snapshots&gt;
	&lt;/repository&gt;
&lt;/repositories&gt;
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<dependencies>
	<dependency>
		<artifactId>nanohttpd</artifactId>
		<groupId>org.nanohttpd</groupId>
		<version>XXXXX-SNAPSHOT</version>
	</dependency>
</dependencies>
...
<repositories>
	<repository>
		<id>sonatype-snapshots</id>
		<url>https://oss.sonatype.org/content/repositories/snapshots</url>
		<snapshots>
			<enabled>true</enabled>
		</snapshots>
	</repository>
</repositories>" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生成自签名 SSL 证书</font></font></h3><a id="user-content-generating-an-self-signed-ssl-certificate" class="anchor" aria-label="永久链接：生成自签名 SSL 证书" href="#generating-an-self-signed-ssl-certificate"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只是提示如何为本地主机生成证书。</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>keytool -genkey -keyalg RSA -alias selfsigned -keystore keystore.jks -storepass password -validity 360 -keysize 2048 -ext SAN=DNS:localhost,IP:127.0.0.1  -validity 9999
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="keytool -genkey -keyalg RSA -alias selfsigned -keystore keystore.jks -storepass password -validity 360 -keysize 2048 -ext SAN=DNS:localhost,IP:127.0.0.1  -validity 9999" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这将为 IP 地址为 127.0.0.1 的名为 localhost 的主机生成一个名为“keystore.jks”的密钥库文件，其中包含自签名证书。</font><font style="vertical-align: inherit;">现在您可以使用：</font></font></p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>server.makeSecure(NanoHTTPD.makeSSLSocketFactory("/keystore.jks", "password".toCharArray()), null);
</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="server.makeSecure(NanoHTTPD.makeSSLSocketFactory(&quot;/keystore.jks&quot;, &quot;password&quot;.toCharArray()), null);" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在启动服务器以使 NanoHTTPD 提供 HTTPS 连接之前，请确保“keystore.jks”位于类路径中。</font></font></p>
<hr>
<p dir="auto"><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">感谢所有报告错误和建议修复的人。</font></font></em></p>
</article></div>
