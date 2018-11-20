---
title: Optimisation de votre code Azure dans Visual Studio | Microsoft Docs
description: En savoir plus sur le fonctionnement d’Azure code outils d’optimisation dans Visual Studio vous aider à rendre votre code plus robuste et plus performant.
author: ghogen
manager: douge
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: d1d0f5a69015a6c6596e1a2b7ee85b12f4116d6b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001776"
---
# <a name="optimizing-your-azure-code"></a>Optimisation de votre code Azure
Quand vous programmez des applications qui utilisent Microsoft Azure, il existe certaines pratiques de codage que vous devez suivre pour vous aider à éviter les problèmes d’évolutivité de l’application, les comportements et les performances dans un environnement de cloud. Microsoft fournit un outil Azure Code Analysis qui reconnaît et identifie plusieurs de ces problèmes couramment rencontrés et vous permet de les résoudre. Vous pouvez télécharger l’outil dans Visual Studio via NuGet.

## <a name="azure-code-analysis-rules"></a>Règles d’analyse du Code Azure
L’outil Azure Code Analysis utilise les règles suivantes pour marquer automatiquement votre code Azure lorsqu’il détecte des problèmes connus affectant les performances. Problèmes détectés apparaissent comme des avertissements ou erreurs du compilateur. Correctifs de code ou des suggestions pour résoudre l’avertissement ou l’erreur sont souvent fournies via une icône d’ampoule.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Évitez d’utiliser le mode d’état de session (in-process) par défaut
### <a name="id"></a>Id
AP0000

### <a name="description"></a>Description
Si vous utilisez le mode d’état de session (in-process) par défaut pour les applications cloud, vous risquez de perdre l’état de session.

Partagez vos idées et les commentaires en [commentaires d’analyse de Code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Par défaut, le mode d’état de session spécifié dans le fichier web.config est en cours. En outre, si aucune entrée n’est spécifiée dans le fichier de configuration, le mode d’état de Session par défaut à in-process. Le mode in-process stocke l’état de session en mémoire sur le serveur web. Lorsqu’une instance est redémarrée ou une nouvelle instance est utilisée pour l’équilibrage de charge ou prise en charge du basculement, l’état de session stockée dans la mémoire sur le serveur web n’est pas enregistré. Cette situation empêche l’application d’être évolutive sur le cloud.

État de session ASP.NET prend en charge plusieurs options de stockage différents pour les données d’état de session : InProc, StateServer, SQLServer, personnalisée et la valeur Off. Il est recommandé que vous utilisez le mode personnalisé pour héberger des données dans un magasin d’état de Session externe, tel que [fournisseur d’état de Session Azure pour Redis](http://go.microsoft.com/fwlink/?LinkId=401521).

### <a name="solution"></a>Solution
Une solution recommandée consiste à stocker l’état de session sur un service de cache géré. Découvrez comment utiliser [fournisseur d’état de Session Azure pour Redis](http://go.microsoft.com/fwlink/?LinkId=401521) pour stocker votre état de session. Vous pouvez également stocker l’état de session dans d’autres endroits pour assurer que votre application est évolutive sur le cloud. Pour en savoir plus sur les solutions alternatives, consultez [Modes d’état de Session](https://msdn.microsoft.com/library/ms178586).

## <a name="run-method-should-not-be-async"></a>Méthode d’exécution ne doit pas être asynchrone
### <a name="id"></a>Id
AP1000

### <a name="description"></a>Description
Créez des méthodes asynchrones (telles que [await](https://msdn.microsoft.com/library/hh156528.aspx)) en dehors de la [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) (méthode), puis appelez les méthodes asynchrones depuis [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx). Déclarer la [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) méthode asynchrone provoque le rôle de travail entrer une boucle de redémarrage.

Partagez vos idées et les commentaires en [commentaires d’analyse de Code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Appel de méthodes asynchrones à l’intérieur de la [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) méthode provoque l’exécution du service cloud recycle le rôle de travail. Lorsqu’un rôle de travail démarre, toute l’exécution du programme a lieu à l’intérieur de la [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) (méthode). Quitter le [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) méthode provoque le redémarrage du rôle de travail. Lors de l’exécution du rôle de travail atteint la méthode asynchrone, il répartit toutes les opérations après la méthode asynchrone, puis retourne. Cela entraîne le rôle de travail à quitter le [ [ [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) (méthode) et redémarrage. Dans l’itération suivante de l’exécution, le rôle de travail atteint à nouveau de la méthode asynchrone et redémarre, provoquant le recyclage aussi à nouveau le rôle de travail.

### <a name="solution"></a>Solution
Placez toutes les opérations asynchrones en dehors de la [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) (méthode). Ensuite, appelez la méthode asynchrone refactorisée depuis l’intérieur du [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) méthode, par exemple RunAsync () .wait. L’outil d’analyse de Code Azure peut vous aider à résoudre ce problème.

L’extrait de code suivant montre la correction du code pour ce problème :

```
public override void Run()
{
    RunAsync().Wait();
}

public async Task RunAsync()
{
    //Asynchronous operations code logic
    // This is a sample worker implementation. Replace with your logic.

    Trace.TraceInformation("WorkerRole1 entry point called");

    HttpClient client = new HttpClient();

    Task<string> urlString = client.GetStringAsync("http://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>Utiliser l’authentification de Signature d’accès partagé Service Bus
### <a name="id"></a>Id
AP2000

### <a name="description"></a>Description
Utilisez la Signature d’accès partagé (SAP) pour l’authentification. Access Control Service (ACS) est déconseillé pour l’authentification de service bus.

Partagez vos idées et les commentaires en [commentaires d’analyse de Code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Pour renforcer la sécurité, Azure Active Directory remplace l’authentification ACS avec l’authentification SAP. Consultez [Azure Active Directory est le futur d’ACS](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) pour plus d’informations sur le plan de transition.

### <a name="solution"></a>Solution
Utiliser l’authentification SAP dans vos applications. L’exemple suivant montre comment utiliser un jeton SAS existant pour accéder à un espace de noms service bus ou une entité.

```
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Consultez les rubriques suivantes pour plus d’informations.

* Pour une vue d’ensemble, consultez [accès authentification par Signature partagé avec Service Bus](https://msdn.microsoft.com/library/dn170477.aspx)
* [Comment utiliser l’authentification par Signature d’accès partagé avec Service Bus](https://msdn.microsoft.com/library/dn205161.aspx)
* Pour un exemple de projet, consultez [l’authentification à l’aide de SAS Shared Access Signature () avec les abonnements Service Bus](http://code.msdn.microsoft.com/windowsazure/Using-Shared-Access-e605b37c)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>Envisagez d’utiliser la méthode OnMessage pour éviter de « boucle de réception »
### <a name="id"></a>Id
AP2002

### <a name="description"></a>Description
Pour éviter d’entrer dans une « boucle de réception, » appel de la **OnMessage** méthode est une meilleure solution pour la réception des messages que l’appel le **réception** (méthode). Toutefois, si vous devez utiliser le **réception** (méthode) et que vous spécifiez un délai d’attente de serveur non-par défaut, assurez-vous que le délai d’attente de serveur est plus d’une minute.

Partagez vos idées et les commentaires en [commentaires d’analyse de Code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Lors de l’appel **OnMessage**, le client démarre une pompe de messages interne qui interroge en permanence la file d’attente ou l’abonnement. Cette pompe de messages contient une boucle infinie qui émet un appel pour recevoir des messages. Si l’appel expire, il émet un nouvel appel. L’intervalle de délai d’expiration est déterminé par la valeur de la [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) propriété de la [MessagingFactory](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx)qui est utilisé.

L’avantage d’utiliser **OnMessage** par rapport à **réception** est que les utilisateurs n’ont à interroger pour les messages, gérer les exceptions, traiter plusieurs messages en parallèle et terminer les messages manuellement.

Si vous appelez **réception** sans utiliser sa valeur par défaut, assurez-vous que le *ServerWaitTime* valeur est plus d’une minute. Paramètre *ServerWaitTime* pour plus d’une minute empêche le serveur n’expire pas avant réception complète du message.

### <a name="solution"></a>Solution
Consultez les exemples de code suivants pour les utilisations recommandées. Pour plus d’informations, consultez [QueueClient.OnMessage (méthode) (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx)et [QueueClient.Receive (méthode) (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx).

Pour améliorer les performances de l’infrastructure de messagerie Azure, consultez le modèle de conception [Primer de messagerie asynchrone](https://msdn.microsoft.com/library/dn589781.aspx).

Voici un exemple d’utilisation **OnMessage** pour recevoir des messages.

```
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is recieved, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

Voici un exemple d’utilisation **réception** temps d’attente avec le serveur par défaut.

```
string connectionString =  
CloudConfigurationManager.GetSetting("Microsoft.ServiceBus.ConnectionString");

QueueClient Client =  
    QueueClient.CreateFromConnectionString(connectionString, "TestQueue");

while (true)  
{   
   BrokeredMessage message = Client.Receive();
   if (message != null)
   {
      try  
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +  
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
```

Voici un exemple d’utilisation **réception** temps d’attente avec un serveur non définis par défaut.

```
while (true)  
{   
   BrokeredMessage message = Client.Receive(new TimeSpan(0,1,0));

   if (message != null)
   {
      try  
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +  
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
}
```
## <a name="consider-using-asynchronous-service-bus-methods"></a>Envisagez d’utiliser des méthodes asynchrones de Service Bus
### <a name="id"></a>Id
AP2003

### <a name="description"></a>Description
Utilisez les méthodes asynchrones de Service Bus pour améliorer les performances avec la messagerie répartie.

Partagez vos idées et les commentaires en [commentaires d’analyse de Code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Permet de concurrence de programme d’application à l’aide de méthodes asynchrones, car l’exécution de chaque appel ne bloque pas le thread principal. Lorsque vous utilisez Service Bus messaging méthodes, les opérations (envoi, réception, supprimer, etc.) prend du temps. Cette durée inclut le traitement de l’opération par le Service service Bus en plus de la latence de la demande et la réponse. Pour augmenter le nombre d’opérations par période, les opérations doivent s’exécuter simultanément. Pour plus d’informations, consultez [meilleures pratiques pour les performances des améliorations à l’aide de messagerie répartie Service Bus](https://msdn.microsoft.com/library/azure/hh528527.aspx).

### <a name="solution"></a>Solution
Consultez [classe QueueClient (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx) pour plus d’informations sur l’utilisation de la méthode asynchrone recommandée.

Pour améliorer les performances de l’infrastructure de messagerie Azure, consultez le modèle de conception [Primer de messagerie asynchrone](https://msdn.microsoft.com/library/dn589781.aspx).

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Envisagez le partitionnement des files d’attente Service Bus et des rubriques
### <a name="id"></a>Id
AP2004

### <a name="description"></a>Description
Files d’attente Service Bus de partition et les rubriques pour de meilleures performances avec la messagerie Service Bus.

Partagez vos idées et les commentaires en [commentaires d’analyse de Code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Partitionnement des files d’attente Service Bus et les rubriques d’augmente la disponibilité de débit et le service de performances, car le débit global d’une file d’attente partitionnée ou une rubrique est n’est plus limité par les performances d’un seul courtier de messages ou de la banque de messagerie. En outre, une panne temporaire d’une banque de messagerie ne rend pas une rubrique ou file d’attente partitionnée indisponible. Pour plus d’informations, consultez [partitionnement des entités de messagerie](https://msdn.microsoft.com/library/azure/dn520246.aspx).

### <a name="solution"></a>Solution
L’extrait de code suivant montre comment partitionner des entités de messagerie.

```
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Pour plus d’informations, consultez [partitionnées Service Bus et les rubriques | Blog Microsoft Azure](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) et extraire le [file d’attente de Microsoft Azure Service Bus partitionnée](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) exemple.

## <a name="do-not-set-sharedaccessstarttime"></a>Ne pas définir SharedAccessStartTime
### <a name="id"></a>Id
AP3001

### <a name="description"></a>Description
Vous devez éviter d’utiliser sharedaccessstarttime défini à l’heure actuelle pour démarrer immédiatement la stratégie d’accès partagé. Vous devez uniquement définir cette propriété si vous souhaitez démarrer la stratégie d’accès partagé à une date ultérieure.

Partagez vos idées et les commentaires en [commentaires d’analyse de Code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Synchronisation des horloges provoque une légère différence d’heure entre les centres de données. Par exemple, il serait logique de définition de l’heure de début d’une stratégie de signature d’accès partagé en tant que l’heure actuelle à l’aide de DateTime.Now ou une méthode similaire entraîne la stratégie SAS entrent en vigueur immédiatement. Toutefois, la légère différence d’heure entre les centres de données peut provoquer des problèmes dans la mesure où certains moments de centre de données peuvent être légèrement postérieure à l’heure de début, tandis que d’autres en avance. Par conséquent, la stratégie SAS peut expirer rapidement (ou même immédiatement) si la durée de vie de stratégie est trop faible.

Pour plus d’informations sur l’utilisation de la Signature d’accès partagé sur le stockage Azure, consultez [Introducing Table SAS (Shared Access Signature), file d’attente et mise à jour d’objet Blob SAS - Blog d’équipe Microsoft Azure Storage - accueil - blogs MSDN](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Solution
Supprimez l’instruction qui définit l’heure de début de la stratégie d’accès partagé. L’outil Azure Code Analysis fournit un correctif pour ce problème. Pour plus d’informations sur la gestion de la sécurité, consultez le modèle de conception [modèle Valet Key](https://msdn.microsoft.com/library/dn568102.aspx).

L’extrait de code suivant montre la correction du code pour ce problème.

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Délai d’expiration doit être de plus de cinq minutes stratégie d’accès partagé
### <a name="id"></a>Id
AP3002

### <a name="description"></a>Description
Il peut y avoir autant que cinq minutes de différence dans les horloges entre les centres de données à des emplacements différents en raison d’une condition nommée « décalage d’horloge. » Pour empêcher la SAP jeton de stratégie à partir de la date d’expiration défini plus tôt que prévu, le délai d’expiration à plus de cinq minutes.

Partagez vos idées et les commentaires en [commentaires d’analyse de Code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Synchronisent les centres de données à différents emplacements dans le monde entier par un signal d’horloge. Étant donné que le temps requis pour signal d’horloge à se déplacer vers différents emplacements, il peut y avoir un écart entre les centres de données à différents emplacements géographiques bien que tout est censé être synchronisé. Cette différence peut affecter l’accès partagé début temps et expiration intervalle la stratégie. Par conséquent, pour garantir la stratégie d’accès partagé prend effet immédiatement, ne spécifiez pas l’heure de début. En outre, assurez-vous que le délai d’expiration est de plus de 5 minutes pour empêcher l’expiration anticipée du délai.

Pour plus d’informations sur l’utilisation de la Signature d’accès partagé sur le stockage Azure, consultez [Introducing Table SAS (Shared Access Signature), file d’attente et mise à jour d’objet Blob SAS - Blog d’équipe Microsoft Azure Storage - accueil - blogs MSDN](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Solution
Pour plus d’informations sur la gestion de la sécurité, consultez le modèle de conception [modèle Valet Key](https://msdn.microsoft.com/library/dn568102.aspx).

Voici un exemple de ne pas spécifier une heure de début de stratégie accès partagé.

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Voici un exemple de spécification d’une heure de début de stratégie accès partagé avec une durée d’expiration de stratégie supérieure à cinq minutes.

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
  SharedAccessStartTime = new DateTime(2014,1,20),   
 SharedAccessExpiryTime = new DateTime(2014, 1, 21),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Pour plus d’informations, consultez [créer et utiliser une Signature d’accès partagé](https://msdn.microsoft.com/library/azure/jj721951.aspx).

## <a name="use-cloudconfigurationmanager"></a>Utiliser CloudConfigurationManager
### <a name="id"></a>Id
AP4000

### <a name="description"></a>Description
À l’aide de la [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) classe pour les projets, tels que les sites Web Azure et des services mobiles Azure ne présentent aucun problème d’exécution. Comme meilleure pratique, toutefois, il est judicieux d’utiliser Cloud[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) une façon unifiée pour gérer les configurations de toutes les applications de Cloud Azure.

Partagez vos idées et les commentaires en [commentaires d’analyse de Code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
CloudConfigurationManager lit le fichier de configuration approprié pour l’environnement d’application.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>Solution
Refactorisez votre code pour utiliser le [classe CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx). Un correctif de code pour ce problème est fourni par l’outil Azure Code Analysis.

L’extrait de code suivant montre la correction du code pour ce problème. Remplacer

`var settings = ConfigurationManager.AppSettings["mySettings"];`

par

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Voici un exemple montrant comment stocker le paramètre de configuration dans un fichier App.config ou Web.config. Ajoutez les paramètres à la section appSettings du fichier de configuration. Voici le fichier Web.config pour l’exemple de code précédent.

```
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>  
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Évitez d’utiliser des chaînes de connexion codées en dur
### <a name="id"></a>Id
AP4001

### <a name="description"></a>Description
Si vous utilisez des chaînes de connexion codées en dur et vous devez les mettre à jour plus tard, vous devrez apporter des modifications à votre code source et recompiler l’application. Toutefois, si vous stockez vos chaînes de connexion dans un fichier de configuration, vous pouvez modifier les ultérieurement en mettant simplement à jour le fichier de configuration.

Partagez vos idées et les commentaires en [commentaires d’analyse de Code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Coder en dur les chaînes de connexion est une mauvaise pratique, car il présente des problèmes lorsque les chaînes de connexion doivent être modifiées rapidement. En outre, si le projet doit être archivé pour contrôle de code source, les chaînes de connexion codées en dur introduisent des failles de sécurité dans la mesure où les chaînes peuvent être affichés dans le code source.

### <a name="solution"></a>Solution
Store les chaînes de connexion dans les fichiers de configuration ou les environnements Azure.

* Pour les applications autonomes, utilisez app.config pour stocker les paramètres de chaîne de connexion.
* Pour les applications web hébergé par IIS, utilisez web.config pour stocker des chaînes de connexion.
* Pour les applications ASP.NET vNext, utilisez configuration.json pour stocker des chaînes de connexion.

Pour plus d’informations sur l’utilisation de fichiers de configuration comme web.config ou app.config, consultez [conseils de Configuration ASP.NET Web](https://msdn.microsoft.com/library/vstudio/ff400235\(v=vs.100\).aspx). Pour plus d’informations sur la façon dont Azure travail de variables d’environnement, consultez [Sites Web Azure : fonctionnement des chaînes d’Application et utiliser des chaînes de connexion](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Pour plus d’informations sur le stockage de chaîne de connexion dans le contrôle de code source, consultez [éviter de placer des informations sensibles telles que des chaînes de connexion dans les fichiers qui sont stockés dans le référentiel de code source](http://www.asp.net/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Utiliser le fichier de configuration de diagnostics
### <a name="id"></a>Id
AP5000

### <a name="description"></a>Description
Au lieu de configurer les paramètres de diagnostic dans votre code, par exemple à l’aide de l’API de programmation Microsoft.WindowsAzure.Diagnostics, vous devez configurer les paramètres de diagnostic dans le fichier diagnostics.wadcfg. (Ou diagnostics.wadcfgx si vous utilisez Azure SDK 2.5). Ce faisant, vous pouvez modifier les paramètres de diagnostic sans avoir à recompiler votre code.

Partagez vos idées et les commentaires en [commentaires d’analyse de Code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Avant Azure SDK 2.5 (qui utilise Azure diagnostics 1.3), Azure Diagnostics (WAD) pouvait être configuré à l’aide de différentes méthodes : ajout de l’objet blob de configuration dans le stockage, à l’aide du code impératif, une configuration déclarative ou la valeur par défaut configuration. Toutefois, la meilleure façon de configurer les diagnostics consiste à utiliser un fichier de configuration XML (diagnostics.wadcfg ou Diagnostics.wadcfgx pour le SDK 2.5 et versions ultérieures) dans le projet d’application. Dans cette approche, le fichier diagnostics.wadcfg complètement définit la configuration et peut être mis à jour et redéployé à volonté. Combiner l’utilisation du fichier de configuration diagnostics.wadcfg avec les méthodes de programmation de définition de configuration à l’aide de la [DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)ou [RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx)classes peuvent prêter à confusion. Consultez [initialiser ou modifier la Configuration Azure Diagnostics](https://msdn.microsoft.com/library/azure/hh411537.aspx) pour plus d’informations.

Depuis WAD 1.3 (fourni avec Azure SDK 2.5), il n’est plus possible d’utiliser du code pour configurer les diagnostics. Par conséquent, vous pouvez fournir uniquement la configuration lors de l’application ou la mise à jour de l’extension de diagnostics.

### <a name="solution"></a>Solution
Utilisez le Concepteur de configuration de diagnostics pour déplacer les paramètres de diagnostics vers le fichier de configuration de diagnostics (Diagnostics.wadcfg ou Diagnostics.wadcfgx pour le Kit de développement logiciel 2.5 et versions ultérieures). Il est également recommandé d’installer [Azure SDK 2.5](http://go.microsoft.com/fwlink/?LinkId=513188) et utiliser la fonctionnalité de diagnostic plus récente.

1. Dans le menu contextuel pour le rôle que vous souhaitez configurer, choisissez Propriétés, puis l’onglet Configuration.
2. Dans le **Diagnostics** section, assurez-vous que le **activer les Diagnostics** case à cocher est activée.
3. Choisissez le **configurer** bouton.

   ![Accès à l’option Activer les Diagnostics](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Consultez [configuration des Diagnostics pour Azure Cloud Services et Machines virtuelles](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) pour plus d’informations.

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Évitez de déclarer les objets DbContext comme statiques
### <a name="id"></a>Id
AP6000

### <a name="description"></a>Description
Pour économiser de la mémoire, évitez de déclarer les objets DBContext comme statiques.

Partagez vos idées et les commentaires en [commentaires d’analyse de Code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Les objets DBContext contiennent les résultats de requête à partir de chaque appel. Les objets DBContext statiques ne sont pas supprimés jusqu'à ce que le domaine d’application est déchargé. Par conséquent, un objet DBContext statique peut consommer de grandes quantités de mémoire.

### <a name="solution"></a>Solution
Déclarer DBContext comme variable locale ou champ d’instance non statique, utilisez-le pour une tâche, puis laisser être supprimé après utilisation.

L’exemple suivant classe de contrôleur MVC montre comment utiliser l’objet DBContext.

```
public class BlogsController : Controller
    {
        //BloggingContext is a subclass to DbContext        
        private BloggingContext db = new BloggingContext();
        // GET: Blogs
        public ActionResult Index()
        {
            //business logics…
            return View();
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
```

## <a name="next-steps"></a>Étapes suivantes
Pour en savoir plus sur l’optimisation et dépannage des applications Azure, consultez [dépanner une application web dans Azure App Service à l’aide de Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
