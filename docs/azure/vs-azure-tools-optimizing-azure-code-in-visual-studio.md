---
title: Optimisation de votre code Azure
description: Découvrez comment les outils d'optimisation du code Azure dans Visual Studio peuvent rendre votre code plus robuste et plus performant.
author: ghogen
manager: jillfra
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: seodec18
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.prod: visual-studio-dev15
ms.openlocfilehash: a85a74907f36057d52257688960b897724a06502
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55139716"
---
# <a name="optimizing-your-azure-code"></a>Optimisation de votre code Azure
Quand vous programmez des applications qui utilisent Microsoft Azure, nous vous recommandons de suivre certaines pratiques de codage pour éviter des problèmes relatifs à l’évolutivité, au comportement et à la performance dans un environnement cloud. Microsoft fournit un outil Azure Code Analysis, qui reconnaît et identifie plusieurs des problèmes couramment rencontrés et qui vous aide à les résoudre. Vous pouvez télécharger l'outil dans Visual Studio via NuGet.

## <a name="azure-code-analysis-rules"></a>Règles d’Azure Code Analysis
L’outil Azure Code Analysis utilise les règles suivantes pour marquer automatiquement votre code quand il trouve des problèmes connus ayant un impact sur la performance. Les problèmes détectés apparaissent sous la forme d’avertissements ou d’erreurs du compilateur. Des corrections du code ou des suggestions pour résoudre l’avertissement ou l’erreur sont souvent fournis via une icône d’ampoule.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Évitez d'utiliser le mode d'état de session (in-process) par défaut
### <a name="id"></a>Id
AP0000

### <a name="description"></a>Description
Si vous utilisez le mode d’état de session (in-process) par défaut pour les applications cloud, vous pouvez perdre l’état de la session.

Pensez à partager vos idées et vos commentaires sur la page [Commentaires d’analyse du code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motif
Par défaut, le mode d’état de session spécifié dans le fichier web.config est in-process. En outre, si aucune entrée n’est spécifiée dans le fichier de configuration, le mode d’état de session par défaut passe à in-process. Le mode in-process stocke l’état de la session en mémoire sur le serveur web. Lorsqu’une instance est redémarrée ou qu’une nouvelle instance est utilisée pour l’équilibrage de charge ou la prise en charge du basculement, l’état de session stocké en mémoire sur le serveur web n’est pas enregistré. Cette situation bloque l’évolutivité de l’application dans le cloud.

L’état de session ASP.NET prend en charge plusieurs options de stockage différentes pour les données d’état de session : InProc, StateServer, SQLServer, Custom et Off. Il est recommandé d’utiliser le mode personnalisé pour héberger les données dans un magasin externe d’état de session, par exemple le [fournisseur d’état de session Azure pour Redis](http://go.microsoft.com/fwlink/?LinkId=401521).

### <a name="solution"></a>Solution
Une solution recommandée consiste à stocker l’état de session sur un service de cache géré. Découvrez commet utiliser le [fournisseur d'état de session Azure pour Redis](http://go.microsoft.com/fwlink/?LinkId=401521) pour stocker l'état de votre session. Vous pouvez également stocker l’état de session dans d’autres endroits pour assurer l’évolutivité de votre application dans le cloud. Pour en savoir plus sur les solutions alternatives, consultez la page [Modes d'état de session](https://msdn.microsoft.com/library/ms178586).

## <a name="run-method-should-not-be-async"></a>La méthode d'exécution ne doit pas être asynchrone
### <a name="id"></a>Id
AP1000

### <a name="description"></a>Description
Créez des méthodes asynchrones (comme [await](https://msdn.microsoft.com/library/hh156528.aspx)) en dehors de la méthode [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx), puis appelez les méthodes asynchrones depuis [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx). La déclaration de la méthode [[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) comme méthode asynchrone provoque l’entrée du rôle de travail dans une boucle de redémarrage.

Pensez à partager vos idées et vos commentaires sur la page [Commentaires d’analyse du code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
L’appel de méthodes asynchrones à l’intérieur de la méthode [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) fait que l’exécution du service cloud recycle le rôle de travail. Quand un rôle de travail démarre, toute l’exécution du programme se fait à l’intérieur de la méthode [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) . Le fait de quitter la méthode [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) provoque le redémarrage du rôle de travail. Quand l’exécution du rôle de travail atteint la méthode asynchrone, il répartit toutes les opérations après la méthode asynchrone puis se termine. Ainsi, le rôle de travail quitte la méthode [[[[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) et redémarre. Dans l’itération suivante de l’exécution, le rôle de travail atteint à nouveau la méthode asynchrone et redémarre, provoquant aussi à nouveau le recyclage du rôle de travail.

### <a name="solution"></a>Solution
Placez toutes les opérations asynchrones en dehors de la méthode [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) . Ensuite, appelez la méthode asynchrone refactorisée depuis l'intérieur de la méthode [[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) , par exemple RunAsync().wait. L'outil d'analyse du code Azure peut vous aider à résoudre ce problème.

L’extrait de code suivant montre la correction du code pour ce problème :

```csharp
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

## <a name="use-service-bus-shared-access-signature-authentication"></a>Utiliser l’authentification de signature d’accès partagé Service Bus
### <a name="id"></a>Id
AP2000

### <a name="description"></a>Description
Utilisez la signature d’accès partagé (SAP) pour l’authentification. Le service de contrôle d’accès (ACS) est obsolète pour l’authentification Service Bus.

Pensez à partager vos idées et vos commentaires sur la page [Commentaires d’analyse du code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Pour une sécurité renforcée, Azure Active Directory remplace l’authentification du service de contrôle d’accès (ACS) par l’authentification de signature d’accès partagé (SAP). Consultez [Azure Active Directory est le futur d’ACS](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) pour des informations sur le plan de transition.

### <a name="solution"></a>Solution
Utilisez l’authentification de signature d’accès partagé dans vos applications. L’exemple suivant montre comment utiliser un jeton de signature d’accès partagé pour accéder à un espace de noms ou à une entité Service Bus.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Pour plus d’informations, consultez les rubriques suivantes.

* Pour une vue d’ensemble, consultez [Authentification de signature d’accès partagé avec Service Bus](https://msdn.microsoft.com/library/dn170477.aspx)
* [Comment utiliser l’authentification par signature d’accès partagé avec Service Bus](https://msdn.microsoft.com/library/dn205161.aspx)
* Pour un exemple de projet, consultez [Utilisation de l’authentification de signature d’accès partagé avec des abonnements Service Bus](http://code.msdn.microsoft.com/windowsazure/Using-Shared-Access-e605b37c)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>Envisagez d'utiliser la méthode OnMessage pour éviter l’erreur de « boucle de réception »
### <a name="id"></a>Id
AP2002

### <a name="description"></a>Description
Pour éviter d’entrer dans une « boucle de réception », l’appel de la méthode **OnMessage** est une meilleure solution pour la réception des messages que l’appel de la méthode **Receive**. Toutefois, si vous devez utiliser la méthode **Receive** et que vous spécifiez un délai d’attente de serveur autre que celui par défaut, vérifiez que le délai d’attente de serveur est de plus d’une minute.

Pensez à partager vos idées et vos commentaires sur la page [Commentaires d’analyse du code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Lors de l’appel de **OnMessage**, le client démarre une pompe de messages interne qui interroge en permanence la file d’attente ou l’abonnement. Cette pompe de messages contient une boucle infinie qui émet un appel pour recevoir des messages. Dès que l’appel expire, il émet un nouvel appel. L’intervalle de délai d’expiration est déterminé par la valeur de la propriété [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) de [MessagingFactory](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx) utilisée.

L’avantage de l’utilisation de **OnMessage** par rapport à **Receive** est que les utilisateurs n’ont pas besoin d’opération manuelle pour vérifier les messages, gérer les exceptions, traiter plusieurs messages en parallèle et terminer les messages.

Si vous appelez **Receive** sans utiliser sa valeur par défaut, assurez-vous que la valeur *ServerWaitTime* est de plus d’une minute. Si la valeur de *ServerWaitTime* est de plus d’une minute, le serveur n’expire pas avant réception complète du message.

### <a name="solution"></a>Solution
Consultez les exemples de code suivants pour les utilisations recommandées. Pour plus d’informations, consultez [QueueClient.OnMessage (méthode) (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx) et [QueueClient.Receive (méthode) (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx).

Pour améliorer les performances de l’infrastructure de messagerie Azure, consultez le modèle de conception [Notions fondamentales sur la messagerie asynchrone](https://msdn.microsoft.com/library/dn589781.aspx).

Voici un exemple d’utilisation de **OnMessage** pour recevoir des messages.

```csharp
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is received, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

Voici un exemple d’utilisation de **Receive** avec le temps d’attente de serveur par défaut.

```csharp
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

Voici un exemple d’utilisation de **Receive** avec un délai d’attente de serveur autre que celui par défaut.

```csharp
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
## <a name="consider-using-asynchronous-service-bus-methods"></a>Envisagez d'utiliser les méthodes asynchrones de Service Bus
### <a name="id"></a>Id
AP2003

### <a name="description"></a>Description
Les méthodes asynchrones de Service Bus permettent d’améliorer les performances avec la messagerie répartie.

Pensez à partager vos idées et vos commentaires sur la page [Commentaires d’analyse du code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Les méthodes asynchrones permettent l’utilisation simultanée de programmes d’application, car l’exécution de chaque appel ne bloque pas le thread principal. Lors de l’utilisation des méthodes de messagerie Service Bus, les opérations (envoi, réception, suppression, etc.) prennent du temps. Ce temps comprend le traitement de l’opération par le service Service Bus en plus de la latence de la demande et de la réponse. Pour augmenter le nombre d’opérations par période, les opérations doivent s’exécuter simultanément. Pour plus d’informations, consultez [Meilleures pratiques relatives aux améliorations de performances à l’aide de la messagerie répartie Service Bus](https://msdn.microsoft.com/library/azure/hh528527.aspx).

### <a name="solution"></a>Solution
Voir [Classe QueueClient (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx) pour plus d’informations sur l’utilisation de la méthode asynchrone recommandée.

Pour améliorer les performances de l’infrastructure de messagerie Azure, consultez le modèle de conception [Notions fondamentales sur la messagerie asynchrone](https://msdn.microsoft.com/library/dn589781.aspx).

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Envisagez de partitionner les files d’attente et les rubriques Service Bus
### <a name="id"></a>Id
AP2004

### <a name="description"></a>Description
Partitionnement des files d’attente et des rubriques Service Bus pour de meilleures performances avec la messagerie Service Bus.

Pensez à partager vos idées et vos commentaires sur la page [Commentaires d’analyse du code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Le partitionnement des rubriques et des files d’attente Service Bus améliore les performances et la disponibilité du service, car le débit global d’une file d’attente ou d’une rubrique partitionnée n’est plus limité par les performances d’un seul répartiteur ou magasin de messagerie. En outre, la panne temporaire d’un magasin de messagerie ne rend pas une rubrique ou une file d’attente partitionnée indisponible. Pour plus d’informations, consultez la rubrique [Partitionnement des entités de messagerie](https://msdn.microsoft.com/library/azure/dn520246.aspx).

### <a name="solution"></a>Solution
L’extrait de code suivant vous explique comment partitionner des entités de messagerie.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Pour plus d’informations, consultez [Files d’attente et rubriques Service Bus partitionnées | Blog Microsoft Azure](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) et consultez l’exemple de [file d’attente Microsoft Azure Service Bus partitionnée](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f).

## <a name="do-not-set-sharedaccessstarttime"></a>Ne pas définir SharedAccessStartTime
### <a name="id"></a>Id
AP3001

### <a name="description"></a>Description
Évitez d’utiliser SharedAccessStartTime défini à l’heure actuelle pour démarrer immédiatement la stratégie d’accès partagé. Ne définissez cette propriété que si vous voulez démarrer la stratégie d’accès partagé ultérieurement.

Pensez à partager vos idées et vos commentaires sur la page [Commentaires d’analyse du code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
La synchronisation de l’heure provoque une légère différence d’heure entre les centres de données. Par exemple, il serait logique de définir l’heure de début d’une stratégie de signature d’accès partagé à l’heure actuelle avec DateTime.Now ou une méthode similaire, pour faire en sorte que la stratégie de signature d’accès partagé prenne effet immédiatement. Cependant, la légère différence d’heure entre les différents centres de données peut provoquer des problèmes, dans la mesure où certains centres de données peuvent être légèrement en retard par rapport à l’heure de début, tandis que d’autres centres sont en avance. La stratégie de signature d’accès partagé peut donc expirer rapidement (voire immédiatement) si la durée de vie de la stratégie est trop courte.

Pour plus d’informations sur l’utilisation de la signature d’accès partagé sur le stockage Azure, consultez [Présentation de la table SAS (Shared Access Signature), de la file d’attente SAS et de la mise à jour d’objet blob SAS - Blog de l’équipe Microsoft Azure Storage - Accueil - Blogs MSDN](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Solution
Supprimez l’instruction qui définit l’heure de début de la stratégie de signature d’accès partagé. L’outil Azure Code Analysis fournit une correction de ce problème. Pour plus d’informations sur la gestion de la sécurité, consultez le modèle de conception [Modèle Valet Key](https://msdn.microsoft.com/library/dn568102.aspx).

L’extrait de code suivant décrit la correction du code pour ce problème.

```csharp
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

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Le délai d'expiration de la stratégie d'accès partagé doit être de plus de cinq minutes
### <a name="id"></a>Id
AP3002

### <a name="description"></a>Description
Il peut y avoir jusqu’à cinq minutes de différence entre les horloges des différents centres de données en raison d’un problème appelé « décalage d’horloge ». Pour empêcher l’expiration anticipée du jeton de stratégie SAS, définissez le délai d’expiration à plus de cinq minutes.

Pensez à partager vos idées et vos commentaires sur la page [Commentaires d’analyse du code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Les centres de données à différents endroits du monde sont synchronisés selon un signal d’horloge. Étant donné que le signal d’horloge prend un certain temps pour voyager d’un emplacement à l’autre, il peut y avoir un écart entre les centres de données dans les différents emplacements géographiques, même si tout est censé être synchronisé. Cette différence peut affecter l’heure de début de la stratégie d’accès partagé et l’expiration du délai. Par conséquent, pour garantir l’effet immédiat de la stratégie d’accès partagé, ne spécifiez pas d’heure de début. En outre, assurez-vous que le délai d’expiration est supérieur à 5 minutes pour empêcher l’expiration anticipée du délai.

Pour plus d’informations sur l’utilisation de la signature d’accès partagé sur le stockage Azure, consultez [Présentation de la table SAS (Shared Access Signature), de la file d’attente SAS et de la mise à jour d’objet blob SAS - Blog de l’équipe Microsoft Azure Storage - Accueil - Blogs MSDN](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Solution
Pour plus d’informations sur la gestion de la sécurité, consultez le modèle de conception [Modèle Valet Key](https://msdn.microsoft.com/library/dn568102.aspx).

Voici un exemple présentant comment ne pas spécifier une heure de début de la stratégie d’accès partagé.

```csharp
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

Voici un exemple présentant comment spécifier une heure de début de la stratégie d’accès partagé avec une durée d’expiration de stratégie supérieure à cinq minutes.

```csharp
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

Pour plus d'informations, consultez [Créer et utiliser une signature d’accès partagé](https://msdn.microsoft.com/library/azure/jj721951.aspx).

## <a name="use-cloudconfigurationmanager"></a>Utiliser CloudConfigurationManager
### <a name="id"></a>Id
AP4000

### <a name="description"></a>Description
L’utilisation de la classe [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) pour les projets comme les sites web Azure et les services mobiles Azure ne présente aucun problème d’exécution. Il est toutefois conseillé d’utiliser Cloud[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) de façon unifiée pour gérer les configurations de toutes les applications cloud Azure.

Pensez à partager vos idées et vos commentaires sur la page [Commentaires d’analyse du code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
CloudConfigurationManager lit le fichier de configuration approprié pour l’environnement de l’application.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>Solution
Refactorisez votre code pour qu’il utilise la [classe CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx). Une correction du code pour ce problème est fournie par l’outil Azure Code Analysis.

L’extrait de code suivant décrit la correction du code pour ce problème. Replace

`var settings = ConfigurationManager.AppSettings["mySettings"];`

par

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Voici un exemple de comment stocker le paramètre de configuration dans un fichier App.config ou Web.config. Ajoutez les paramètres à la section appSettings du fichier de configuration. Voici le fichier Web.config pour l'exemple de code précédent.

```xml
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Évitez d'utiliser des chaînes de connexion codées en dur
### <a name="id"></a>Id
AP4001

### <a name="description"></a>Description
Si vous utilisez des chaînes de connexion codées en dur et que vous devez effectuer une mise à jour ultérieurement, vous devrez apporter des modifications à votre code source et recompiler l’application. Si vous stockez vos chaînes de connexion dans un fichier de configuration, il suffit de mettre à jour le fichier de configuration.

Pensez à partager vos idées et vos commentaires sur la page [Commentaires d’analyse du code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Le codage des chaînes de connexion en dur est une mauvaise pratique, car elle présente des problèmes lorsque les chaînes de connexion doivent être modifiées rapidement. En outre, si le projet doit être archivé pour contrôle du code source, les chaînes de connexion codées en dur introduisent des vulnérabilités de sécurité dans la mesure où ces chaînes peuvent être consultées dans le code source.

### <a name="solution"></a>Solution
Stocker les chaînes de connexion dans les fichiers de configuration ou dans les environnements Azure.

* Pour les applications autonomes, utilisez app.config pour stocker les paramètres de chaîne de connexion.
* Pour les applications web hébergées par IIS, utilisez web.config pour stocker les chaînes de connexion.
* Pour les applications ASP.NET vNext, utilisez configuration.json pour stocker les chaînes de connexion.

Pour plus d’informations sur l’utilisation de fichiers de configuration comme web.config ou app.config, consultez la page [Conseils de configuration ASP.NET web](https://msdn.microsoft.com/library/vstudio/ff400235\(v=vs.100\).aspx). Pour plus d’informations sur le fonctionnement des variables d’environnement Azure, consultez [Sites web Azure : How Application Strings and Connection Strings Work](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/) (Fonctionnement des chaînes d’application et de connexion d’Azure Web Apps). Pour plus d’informations sur le stockage de la chaîne de connexion dans le contrôle de code source, consultez la rubrique [Éviter de placer des informations sensibles (par exemple, des chaînes de connexion) dans des fichiers stockés dans des référentiels de code source](http://www.asp.net/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Utiliser le fichier de configuration des diagnostics
### <a name="id"></a>Id
AP5000

### <a name="description"></a>Description
Au lieu de configurer les paramètres de diagnostic dans votre code, par exemple à l’aide de l’API de programmation Microsoft.WindowsAzure.Diagnostics, vous devez configurer les paramètres de diagnostic dans le fichier diagnostics.wadcfg (ou diagnostics.wadcfgx si vous utilisez Azure SDK 2.5). Vous pouvez ainsi modifier les paramètres de diagnostic sans avoir à recompiler votre code.

Pensez à partager vos idées et vos commentaires sur la page [Commentaires d’analyse du code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Avant Azure SDK 2.5 (qui utilise Azure Diagnostics 1.3), Azure Diagnostics (WAD) pouvait être configuré via différentes méthodes, notamment en l’ajoutant à l’objet blob de configuration dans le stockage en utilisant du code impératif, une configuration déclarative ou la configuration par défaut. Toutefois, la meilleure façon de configurer les diagnostics consiste à utiliser un fichier config XML (diagnostics.wadcfg ou diagnostics.wadcfgx pour le kit SDK 2.5 et les versions ultérieures) dans le projet d’application. Dans cette approche, le fichier diagnostics.wadcfg définit complètement la configuration, et peut être mis à jour et redéployé à volonté. Combiner l’utilisation du fichier de configuration diagnostics.wadcfg avec les méthodes de définition de configuration par programmation à l’aide des classes [DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx) ou [RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx) peut engendrer une certaine confusion. Consultez la rubrique [Initialiser ou modifier la configuration des diagnostics Azure](https://msdn.microsoft.com/library/azure/hh411537.aspx) pour plus d’informations.

Depuis WAD 1.3 (fourni avec Azure SDK 2.5), il n’est plus possible d’utiliser le code pour configurer le diagnostic. Par conséquent, vous pouvez fournir uniquement la configuration lors de l’application ou de la mise à jour de l’extension de diagnostic.

### <a name="solution"></a>Solution
Utilisez le concepteur de configuration de diagnostic pour déplacer les paramètres de diagnostic vers le fichier config de diagnostic (diagnostics.wadcfg ou diagnostics.wadcfgx pour le kit SDK 2.5 et ultérieur). Il est également recommandé d'installer [Azure SDK 2.5](http://go.microsoft.com/fwlink/?LinkId=513188) et d’utiliser la fonctionnalité de diagnostic plus récente.

1. Dans le menu contextuel du rôle que vous voulez configurer, choisissez Propriétés, puis sélectionnez l’onglet Configuration.
2. Dans la section **Diagnostics**, vérifiez que la case à cocher **Activer les diagnostics** est activée.
3. Cliquez sur le bouton **Configurer** .

   ![Accès à l’option Activer les diagnostics](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Consultez [Configuration des diagnostics pour Azure Cloud Services et Azure Virtual Machines](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) pour plus d’informations.

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Éviter de déclarer les objets DbContext comme statiques
### <a name="id"></a>Id
AP6000

### <a name="description"></a>Description
Pour économiser la mémoire, évitez de déclarer les objets DBContext comme statiques.

Pensez à partager vos idées et vos commentaires sur la page [Commentaires d’analyse du code Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Raison
Les objets DBContext contiennent les résultats de requête de chaque appel. Les objets DBContext statiques ne sont pas supprimés jusqu’à ce que le domaine d’application soit déchargé. Par conséquent, un objet DBContext statique peut consommer de grandes quantités de mémoire.

### <a name="solution"></a>Solution
Déclarer DBContext comme variable locale ou champ d’instance non statique, l’utiliser pour une tâche et le laisser être supprimé après utilisation.

L’exemple de classe de contrôleur MVC suivant montre comment utiliser l’objet DBContext.

```csharp
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
Pour plus d’informations sur l’optimisation et le dépannage des applications Azure, consultez la rubrique [Dépanner une application web dans Azure App Service à l’aide de Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
