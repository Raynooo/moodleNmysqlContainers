FROM mysql/mysql-server:5.7

#Had to change a couple of things from the original entrypoint to follow Moodle's best practices
COPY docker-entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

CMD ["mysqld"]

