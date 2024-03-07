## Proxy Design Pattern
Proxy is a structural design pattern. it enables us to provide an interface between client and the class that client tries to use it. for example there is a class that has a method named download, we want user not to call it over and over again if he/she has download it once, so we can create a proxy class to controll the request of user.

* example one : controlling a request for downloading files 
```typescript
// interface for both proxy class and main class (server class)
interface DownloaderInterface {
  download(path);
}


// the main class (server class)
class FileDownloader implements DownloaderInterface {
  public download(path) {
      
  }
}


// proxy class
class FileDownloaderProxy implements DownloaderInterface {
  private downloader: FileDownloader;
  private cachedFiles = {}; 
  
  constructor() {
    this.downloader = new FileDownloader();
  }

   
  public download(path) {
    if (this.cachedFiles.hasOwnProperty(path)) {
      console.log(`Read ${path} from cache`);

      return this.cachedFiles[path];
    } else {
      const result = this.downloader.download(path);
      this.cachedFiles[path] = result;

      return result;
    }
  }
}
```

* second example : logging before using the service
```python

class AbstractServer(abc.ABC):

	@abc.abstractmethod
	def receive(self):
		pass


class Server(AbstractServer):
	def receive(self):
		print('Processing your request...')
		time.sleep(1)
		print('Done...')


class LogProxy(AbstractServer):
	def __init__(self, server):
		self._server = server

	def receive(self):
		self.logging()
		# ...
		self._server.receive()

	def logging(self):
		with open('log.log', 'a') as log:
			log.write(f'Request {datetime.datetime.now()} \n')


def client_server(server, proxy):
	s = server()
	p = proxy(s)
	p.receive()

if __name__ == '__main__':
	client_server(Server, LogProxy)
``` 



















