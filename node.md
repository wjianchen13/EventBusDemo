# EventBus 细节
subscriptionsByEventType是一个HashMap具体存储类型是Map<Class<?>, CopyOnWriteArrayList<Subscription>>
存储是以事件类型为key，Subscription(subscriber, subscriberMethod)为value的键值对
例如demo的存储如下
MessageEvent -> CopyOnWriteArrayList(Subscription(Object TestActivity1, SubscriberMethod onMessageEvent))

typesBySubscriber是一个HashMap，具体存储的类型是Map<Object, List<Class<?>>>
存储是以订阅对象为key，List<Class<?>>为value的键值对，其中List中存储的是事件类型
例如demo的存储如下
TestActivity1 -> List(MessageEvent)
这个typesBySubscriber就是在调用isRegistered()的时候判断是否注册过了。
