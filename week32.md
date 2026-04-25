#### Prompt
Hi! I’m currently learning English as my second language by speaking and practicing the words here. My first language is Chinese, and I would say my English level is beginner.
My goal is to become fluent in English one day, and I’d like your help with that.
Please make follow paragraph more verbal and sense. Please as hard as you can to try  phrasal verb instead of rare vocabulary because it's much natural than difficult vocabulary and native speaker usually make simple word instead of hard ones. Put the edited contents in code block so that I can directly copy it.

## 20/04/2026
origin content
```
1. I tried to close into the relationship with our company's colleagues, and also picked up strangers on a street. However I found that makes friend in realism is much difficult than online.
2. When I told to a people in realism and I could feel nervous and embarrassed from 對方. In real life people have more warning to stranger but in online people would more like to reach out because there would not be a risk of damage on physicals or emotions.
3. If you don't manage social media, you were almost hard to reach out new friends. That's reason people are forced to post many garbage contents like eat what foods, play somewhere and which AV characters come.
4. Most people take most energy and focus on social media, so I think that's really harder to reach out people in real life today.
5. I think human always seek for most save energy way to do anything. That every thing do on online perfectly matches the requirement so people are more willing to open mind on online.     
```

### GPT modified
1. I tried to get closer to my coworkers and also went out to meet strangers on the street. But I found that making friends in real life is much harder than online.

2. When I talk to people face to face, I can feel nervous and awkward, and they seem a bit uncomfortable too. In real life, people are more on guard around strangers, but online people are more willing to reach out because there’s less risk of getting hurt, either physically or emotionally.

3. If you don’t keep up with social media, it’s really hard to meet new people. That’s why people end up posting a lot of garbage stuff, like what they eat, where they go, or what AV character is coming.

4. Most people put a lot of their time and energy into social media, so I think it’s getting harder to connect with people in real life these days.

5. I think people always look for the easiest way to do things. Doing things online fits that perfectly, so people are more open and relaxed there.
 
## 21/04/2026
origin contents
```
1. After AI compacted software career, I can't fully focus on my work in deep. I started considering what alternative skills that can make me survival in the future.
2. I found that when I had to manually code line by line, I felt disgusting and want to throw the job to AI.
3. I don't know whether another middle age men have the same feeling, I seems to loss interesting for every things, the foods, games and jerk off.
4. After trying pick up strangers on roads, I found leaving message is not enough, you still need to catch her notice from your post, and don't take too much expectation on her response. Most ot time they will always no answer.
5. It don't depend on what she is beauty, it depends on what overlaps are between yours and her life. So when someone didn't answer you, you shouldn't be depressive. That's not only your appearance but also the layer of life in difference.
```

### GPT modified
1. After AI started to shake up the software industry, I can’t fully focus on my work anymore. I’ve started to think about what other skills I can pick up to survive in the future.
2. When I have to write code line by line myself, I feel frustrated and just want to hand it off to AI.
3. I don’t know if other middle-aged men feel the same, but I seem to be losing interest in everything—food, games, even jerk off.
4. After trying to meet strangers on the street, I realized that just leaving a message isn’t enough. You still need to catch their attention, and you shouldn’t expect too much from their response. Most of the time, they won’t reply.
5. It’s not just about whether you're attractive. It’s more about how much your lives overlap. So if someone doesn’t reply, don’t take it too hard. It’s not only about your looks, but also about differences in your layer of life.
 
## 22/04/2026
origin contents
```
1. I got a new request in my work, the requirement is to route clients to certain server according to whitelist.
2. The problem is that regular orders can be process arbitrary and send to backend, but the smart orders need send in order.
3. The current architecture is used two queues to distinct these two type of order. The queue handles the in order orders must has only one consumer to tackle the item in the queue, another one can has many consumers because the finish of items in queue we don't care.
4. This problem is already solved and there are many open source specifically against to it. One of famous tool is named Kafka, it was generated for guaranteeing execute items of a queue in order.
5. I tried to fix single consumer to handle the certain order which needs process in order, similar to Kafka's concept, but I was wrong, I thought too simple and naive, I didn't observe the waiting occur when the consumer pop a item which belong the consumer, then other consumers will waiting for the only one consumer finish, then they can read the next item from queue.  
```

### GPT modified

1. I got a new task at work. The requirement is to route clients to certain servers based on a whitelist.
2. The problem is that regular orders can be handled in any order and sent to the backend, but smart orders need to be processed in sequence.
3. The current setup uses two queues to separate these two types of orders. The queue for ordered tasks has only one consumer to deal with them one by one, while the other queue can have multiple consumers since the order doesn’t matter.
4. This problem has already been solved, and there are many open-source tools for it. One of the most well-known is Kafka, which is designed to make sure messages are handled in order.
5. I tried to fix it by using a single consumer to handle the orders that need to stay in order, kind of like Kafka. But I was wrong—I oversimplified it. I didn’t notice that when one consumer picks up an item, the others have to wait until it finishes before they can move on to the next one.