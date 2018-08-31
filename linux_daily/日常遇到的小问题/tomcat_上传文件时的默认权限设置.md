当使用 `tomcat` 为服务器时，上传文件时的默认权限可能和本地 `umask` 设置不一致，因为 `tomcat` 也有一个 `umask` 设置，通过修改 `tomcat` 的 `umask` 设置可以修改 `tomcat` 上传文件的默认权限，修改位置为：

	、bin/catalina.sh
找到，` umask=xxx `,修改并重启服务器