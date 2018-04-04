## <a name="sign-in-to-azure"></a>Se connecter à Azure
Nous devons nous connecter à Azure pour créer notre environnement de développement. Tapez la commande suivante dans une fenêtre de terminal :
```cmd
az login
```

> [!Note]
> Si vous n’avez pas d’abonnement Azure, vous pouvez créer un [compte gratuit](https://azure.microsoft.com/free).

### <a name="if-you-have-multiple-azure-subscriptions"></a>Si vous avez plusieurs abonnements Azure...
Vous pouvez voir vos abonnements en exécutant la commande suivante : 
```cmd
az account list
```
Recherchez l’abonnement qui présente `isDefault: true` dans la sortie JSON.
Si ce n’est pas l’abonnement que vous voulez utiliser, vous pouvez changer l’abonnement par défaut :
```cmd
az account set --subscription <subscription ID>
```
