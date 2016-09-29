## 利用Redis做整点秒杀抢购
    redis-cli     set miaosha_key 100
下面是伪代码

    <?php
    $redis = Redis::getClient();
    $key = 'miaosha_key';
    $key_r = $redis->decr($key); //最关键
    if ($key_r < 0) {
    
    	echo json_encode(['code' => 0, 'msg' => '已经被抢光']);
    } else {
    	//抢到了
    	//队列或者直接保存数据库
    	echo json_encode(['code' => 1, 'msg' => '抢到了']);
    }
