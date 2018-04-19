##### 进入 /etc/profile  , 在末尾处加上以下代码：


	# 新增访客ip记录
	PS1="`whoami`@`hostname`:"'[$PWD]'
	history
	USER_IP=`who -u am i 2>/dev/null| awk '{print $NF}'|sed -e 's/[()]//g'`
	if [ "$USER_IP" = "" ]
	then
	USER_IP=`hostname`
	fi
	if [ ! -d /tmp/history ]
	then
	mkdir /tmp/history
	chmod 777 /tmp/history
	fi
	if [ ! -d /tmp/history/${LOGNAME} ]
	then
	mkdir /tmp/history/${LOGNAME}
	chmod 300 /tmp/history/${LOGNAME}
	fi
	export HISTSIZE=4096
	DT=`date +"%Y%m%d_%H%M%S"`
	export HISTFILE="/tmp/history/${LOGNAME}/${USER_IP} history.$DT"
	chmod 600 /tmp/history/${LOGNAME}/*history* 2>/dev/null