Provide the symfony 1.4 command line to deploy your app on a server.

## Installation

### Add DeployBundle to your src/Bundle dir

    git submodule add git://github.com/dator/DeployBundle.git src/Bundle/DeployBundle

### Add DeployBundle to your application kernel

    // app/AppKernel.php
    public function registerBundles()
    {
        return array(
            // ...
            new Bundle\DeployBundle\DeployBundle(),
            // ...
        );
    }

### Configure

    # app/config/config.yml
    deploy.config:
      prod:
        host: 127.0.0.1 // or the hostname
        user: root
        dir: /path/to/dir
        port: 22
      stage:
        host: 127.0.0.1 // or the hostname
        user: root2
        dir: /path/to/dir
        port: 22
    
### Rsync Exclude

Create a rsync_exclude.txt file under app/config to exclude files in your deployments.

### Use

Deployment is easy: 

    php app/console project:deploy --go prod

Simulate deployment

    php app/console project:deploy prod

or

    php app/console project:deploy --dry-run prod