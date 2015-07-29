#命令行工具

*  [1.nats-pub](#1)  
*  [2.nats-sub](#2)
*  [3.nats-queue](#3)
*  [4.nats-request](#4)
*  [5.nats-top](#5)

<h2 id="1">1.nats-pub</h2>
<table class="table table-bordered">
   <tr>
      <td><strong>用途</strong></td>
      <td>发送消息，订阅者收到消息后回复</td>
   </tr>
   <tr>
      <td><strong>消息模式 </strong></td>
      <td>发布-订阅</td>
   </tr>
   <tr>
      <td><strong>使用格式</strong> </td>
      <td>nats-request &lt;subject&gt; &lt;msg&gt; [-s server] </td>
   </tr>
      <tr>
      <td><strong>使用示例</strong></td>
      <td>nats-pub "dea.stop" '{"droplet":"fe62dc78-e397-460a-a40b-0e3ddb0db672"}' -s nats://10.20.2.3:4222</td>
   </tr>
   <tr>
      <td><strong>备注</strong></td>
      <td>subject指消息主题，匹配支持通配符>和*<br>-s server 指nats server 的ip:port，使用4222端口</td>
   </tr>
</table>

<h2 id="2">2.nats-sub</h2>
<table class="table table-bordered">
   <tr>
      <td><strong>用途</strong></td>
      <td>订阅消息</td>
   </tr>
   <tr>
      <td><strong>消息模式 </strong></td>
      <td>发布-订阅</td>
   </tr>
   <tr>
      <td><strong>使用格式</strong> </td>
      <td>nats-sub &lt;subject&gt; [-s server] [-t] [-r] </td>
   </tr>
      <tr>
      <td><strong>使用示例</strong></td>
      <td>nats-sub "dea.stop"  -s nats://10.20.2.3:4222 -t</td>
   </tr>
   <tr>
      <td><strong>备注</strong></td>
      <td>subject指消息主题，匹配支持通配符>和*<br>-s server 指nats-server的ip:port，使用4222端口<br>-t指显示接收时间<br>-r指raw模式，只显示消息&lt;msg&gt;内容</td>
   </tr>
</table>

<h2 id="3">3.nats-queue</h2>
<table class="table table-bordered">
   <tr>
      <td><strong>用途</strong></td>
      <td>队列形式订阅消息</td>
   </tr>
   <tr>
      <td><strong>消息模式 </strong></td>
      <td>发布-订阅</td>
   </tr>
   <tr>
      <td><strong>使用格式</strong> </td>
      <td>nats-queue &lt;subject&gt; &lt;queue name&gt;[-s server] [-t] [-r]</td>
   </tr>
      <tr>
      <td><strong>使用示例</strong></td>
      <td>nats-queue 'topic' "queue" -s nats://172.18.8.7:4222 </td>
   </tr>
   <tr>
      <td><strong>备注</strong></td>
      <td>subject指消息主题，匹配支持通配符>和*<br>queue name 指消息的队列名<br>-s server 指nats-server的ip:port<br>-t指显示接收时间<br>-r指raw模式，只显示消息&lt;msg&gt;内</td>
   </tr>
</table>

<h2 id="4">4.nats-request</h2>
<table class="table table-bordered">
   <tr>
      <td><strong>用途</strong></td>
      <td>发送消息，订阅者收到消息后回复</td>
   </tr>
   <tr>
      <td><strong>消息模式 </strong></td>
      <td>发布-订阅</td>
   </tr>
   <tr>
      <td><strong>使用格式</strong> </td>
      <td>nats-request &lt;subject&gt; &lt;msg&gt; [-s server] [-t] [-r] [-n responses]]</td>
   </tr>
      <tr>
      <td><strong>使用示例</strong></td>
      <td>nats-request 'topic' "hello" -s nats://172.18.8.7:4222 -n "2"</td>
   </tr>
   <tr>
      <td><strong>备注</strong></td>
      <td>subject指消息主题，匹配支持通配符>和*<br>-s server 指nats-server的ip:port<br>-t指显示接收时间<br>-r指raw模式，只显示消息&lt;msg&gt;内容<br>-n responses，收到回复的条数，当条数到达时断开</td>
   </tr>
   </table>
   
<h2 id="5">5.nats-top</h2>
<table class="table table-bordered">
   <tr>
      <td><strong>用途</strong></td>
      <td>监控nats使用状态</td>
   </tr>
   <tr>
      <td><strong>使用格式</strong> </td>
      <td>nats-top [-s server_uri] [-m local monitor port] [-n num_connections] [-d delay_secs] [--sort sort_by]</td>
   </tr>
      <tr>
      <td><strong>使用示例</strong></td>
      <td>nats-top -s http://172.18.18.7:4242</td>
   </tr>
   <tr>
      <td><strong>备注</strong></td>
      <td>-s server 指nats-server的ip:port，使用4242端口<br>-m local monitor port 监控端口，默认9222<br>-n num_connections 限制显示的连接数，默认为10<br>-d delay 刷新时间，默认为1<br>--sort sort_by 排序方式，默认以'pending_size'排序，有spending_size, msgs_to,   msgs_from, bytes_to, bytes_from, subs几种排序基准，以数据的从大到小排序</td>
   </tr>
   </table>
