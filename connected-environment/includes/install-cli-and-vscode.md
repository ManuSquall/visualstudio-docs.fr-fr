## <a name="install-the-connected-environment-cli"></a>Installer l’interface CLI Connected Environment
Connected Environment nécessite une installation minimale sur un ordinateur local. L’essentiel de la configuration de votre environnement de développement est stocké dans le cloud et peut être partagé avec d’autres utilisateurs.

### <a name="install-on-mac"></a>Installer sur Mac
Téléchargez et installez l’interface CLI Connected Environment :
```cmd
curl -L https://aka.ms/get-vsce-mac | bash
```

### <a name="install-on-windows"></a>Installer sur Windows
1. Téléchargez et exécutez le [programme d’installation de l’interface CLI Connected Environment](https://aka.ms/get-vsce-windows). 

### <a name="install-on-linux"></a>Installer sur Linux
Bientôt disponible...

## <a name="get-kubernetes-debugging-for-vs-code"></a>Obtenir les fonctionnalités de débogage Kubernetes pour VS Code
En plus de l’interface CLI Connected Environment que vous pouvez utiliser comme outil autonome, il existe des fonctionnalités avancées comme le débogage Kubernetes qui s’adresse aux développeurs .NET Core et Node.js utilisant VS Code.

1. Si vous n’y avez pas accès, installez [VS Code](https://code.visualstudio.com/Download).
1. Téléchargez l’[extension VS Connected Environment](https://aka.ms/get-vsce-code).
1. Installez l’extension : 

```cmd
code --install-extension path-to-downloaded-extension/vsce-0.1.1.vsix
```
