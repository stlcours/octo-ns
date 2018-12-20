##  SGAgent简介  
  
  * SGAgent是基于C++开发的服务治理代理，为美团点评OCTO服务治理体系提供支持水平扩展的RPC/HTTP服务治理接入.
  * SGAgent作为服务端项目基础组件，提供了通过RPC/HTTP进行服务注册、服务发现等功能.
  * SGAgent组件的引入简化了SDK和通信框架的设计，可进行基于标签、服务分组等功能辅助通信框架完成软负载及流量走向定义.

##  功能简介  

  服务治理完成服务注册、服务发现的两个主要流程，注册支持按增量和非增量方式，增量方式是指一个服务实例可以包含多种ServiceName接口类型，通过在注册中心建立ServiceName和服务实例的双向映射，可满足按ServiceName和服务实例两种方式进行服务发现.
  
  (1)**服务分组**：服务分组本质影响服务节点权重(权重的调整可按照用户进行自定义)，服务分组只有在注册中心配置了路由策略且生效才会最终影响到权重过滤，目前支持的几种策略如下

 a.自定义路由分组:在服务端配置该策略后，可定向指定上游打入该服务的服务范围; 

 b.同机房优先分组:是默认分组，自动开启，流量优先在同机房进行调用.

 c.同中心优先分组: 默认不开启，流量在同中心进行调用.

 d.同城市路由分组: 在同域进行流量的调用.

 (2)**标签过滤**: 对于服务提供者自定义了标签属性的服务发现流程，可按照传入标签返回对应感兴趣服务提供者信息.
 
 (3)**HTTP接口**: 支持HTTP接口进行服务发现.