gogo:
	sudo systemctl stop nginx
	sudo systemctl stop isubata.ruby.service
	sudo systemctl stop mysql
	sudo truncate --size 0 /var/log/nginx/access.log
	sudo truncate --size 0 /var/log/nginx/error.log
	sudo systemctl start mysql 
	sudo systemctl start isubata.ruby.service
	sudo systemctl start nginx
	sleep 6
	$(MAKE) bench

bench:
	ssh isucon7-q-bench "cd /home/isucon/isubata/bench && make bench"

