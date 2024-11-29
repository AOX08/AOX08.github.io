<?php
$logFile = 'visitor_log.txt'; // 日志文件名

// 检查日志文件是否存在,如果不存在则创建
if (!file_exists($logFile)) {
    file_put_contents($logFile, "访问次数,访问时间,访问日期\n");
}

// 记录访问信息
$visitorCount = count(file($logFile)) - 1; // 减去标题行
$currentTime = date('H:i:s');
$currentDate = date('Y-m-d');
$logEntry = "$visitorCount,$currentTime,$currentDate\n";
file_put_contents($logFile, $logEntry, FILE_APPEND);

// 输出访问次数
echo "您是第 " . ($visitorCount + 1) . " 位访问者";
?>
