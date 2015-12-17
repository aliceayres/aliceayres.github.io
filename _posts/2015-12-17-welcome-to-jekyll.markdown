---
layout: post
title:  "Jekyll Hello World!"
date:   2015-12-17 18:34:27 +0800
categories: hello world
---
It's my `first` time to heard of Jekyll and to build a blog via git pages.
All were so exciting to deal with.
I called it my `hello world` in Ayres's blog!
Let me try the code snippets:

{% highlight java %}
public class ProtostuffUtil {

	@SuppressWarnings("unchecked")
	public static <T extends MessageLite,C> T ser(T proto, Object obj) throws Exception {
		Class<?> C = obj.getClass();
		Schema<C> schema = (Schema<C>) RuntimeSchema.getSchema(C);
		LinkedBuffer buffer = LinkedBuffer.allocate(1024);
		byte[] data = ProtobufIOUtil.toByteArray((C)obj, schema, buffer);
		ProtobufIOUtil.mergeFrom(data, schema.newMessage(), schema);
		T message = (T) proto.newBuilderForType().mergeFrom(data).build();
		return message;
	}

	public static <T> T deser(MessageLite proto, Class<T> clazz) throws Exception {
		Schema<T> schema = RuntimeSchema.getSchema(clazz);
		T obj = clazz.newInstance();
		ProtobufIOUtil.mergeFrom(proto.toByteArray(), obj, schema);
		return obj;
	}

}
{% endhighlight %}

 If you like it, please remember my first site with Jekyyll -- [Ayres' blog][ayres-blog].

 In the end, sentence of the First day is:
 "A life is like a garden, perfect moments can be had, but not preserved, except in memory."

[ayres-blog]: http://aliceayres.github.io
