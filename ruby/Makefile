gogo:
	sudo systemctl stop nginx
	sudo systemctl stop isubata.ruby.service
	sudo systemctl stop mysql
	sudo truncate --size 0 /var/log/nginx/access.log
	sudo truncate --size 0 /var/log/nginx/error.log
	sudo truncate --size 0 /var/log/mysql/mysql-slow.log
	sudo systemctl start mysql 
	sudo systemctl start isubata.ruby.service
	sudo systemctl start nginx
	sleep 6
	$(MAKE) bench

bench:
	ssh isucon7-q-bench "cd /home/isucon/isubata/bench && make bench"
alp:
	sudo cat /var/log/nginx/access.log | alp ltsv --format=md -m='/fonts/.*,/icons/.*,/channel/[0-9]+,/history/[0-9]+' --sort sum
