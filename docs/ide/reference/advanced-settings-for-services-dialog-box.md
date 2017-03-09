---
title: "Param&#232;tres avanc&#233;s pour les services, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesAdvancedServices"
helpviewer_keywords: 
  - "Paramètres avancés pour la boîte de dialogue Services"
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Param&#232;tres avanc&#233;s pour les services, bo&#238;te de dialogue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les services d'application cliente facilitent l'accès aux services de connexion [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)], de rôles et de services de profil depuis les applications Windows Forms et Windows Presentation Foundation \(WPF\).  Vous pouvez utiliser la page **Services** du **Concepteur de projets** pour configurer des services d'application cliente.  Pour plus d'informations sur la page **Services**, consultez [Services, page du Concepteur de projets](../../ide/reference/services-page-project-designer.md).  
  
 Utilisez la boîte de dialogue **Paramètres avancés pour les services** de la page **Services** du **Concepteur de projets** pour configurer des paramètres avancés pour les services d'application cliente.  Ces paramètres vous permettent de substituer des comportements des services d'application par défaut pour autoriser des scénarios moins courants.  Pour plus d'informations, consultez [Services d'application cliente](../Topic/Client%20Application%20Services.md).  
  
 Pour accéder à la boîte de dialogue **Paramètres avancés pour les services**, sélectionnez un nœud de projet dans l'**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**.  Lorsque le **Concepteur de projets** s'ouvre, cliquez sur l'onglet **Services**, puis sur le bouton **Avancé**.  Ce bouton est désactivé jusqu'à l'activation des services d'application cliente.  
  
## Liste des tâches  
 [Comment : configurer les services d'application cliente](../Topic/How%20to:%20Configure%20Client%20Application%20Services.md)  
  
 [How to: Work Offline with Client Application Services](http://msdn.microsoft.com/fr-fr/f792cb16-8520-4a0f-9dc9-07bfbc454e38)  
  
## Liste UIElement  
 **Enregistrer le hachage de mot de passe localement pour activer la connexion hors connexion**  
 Indique si le mot de passe de l'utilisateur sera mis en cache localement sous une forme chiffrée pour autoriser l'utilisateur à se connecter lorsque l'application est en mode hors connexion.  Pour plus d'informations, consultez [How to: Work Offline with Client Application Services](http://msdn.microsoft.com/fr-fr/f792cb16-8520-4a0f-9dc9-07bfbc454e38).  Cette option est activée par défaut.  
  
 **Imposer aux utilisateurs de se reconnecter chaque fois que le cookie du serveur expire**  
 Indique si des utilisateurs précédemment authentifiés font l'objet d'une nouvelle authentification automatique lorsque votre application accède aux rôles ou services de profil et que le cookie d'authentification du serveur a expiré.  Sélectionnez cette option pour refuser l'accès aux services d'application et exiger une nouvelle authentification après l'expiration du cookie.  Cette option est utile pour les applications déployées dans des lieux publics afin de garantir que les utilisateurs qui quittent l'application en cours d'exécution ne restent pas authentifiés indéfiniment.  Cette option est désactivée par défaut.  
  
 **Dépassement du délai de cache du service de rôle**  
 Indique la durée pendant laquelle le fournisseur de rôles clients utilisera des valeurs de rôle mises en cache au lieu d'accéder au service de rôles.  Choisissez une valeur peu élevée lorsque les rôles sont fréquemment mis à jour ou une valeur plus élevée lorsque les rôles sont rarement mis à jour.  La valeur par défaut est définie à une journée.  
  
 Le fournisseur de rôles accède aux valeurs de rôle mises en cache ou au service de rôles lorsque vous appelez la méthode <xref:System.Web.Security.RolePrincipal.IsInRole%2A>.  Pour vider le cache par programme et forcer cette méthode à accéder au service distant, appelez la méthode <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>.  
  
 **Utiliser une chaîne de connexion personnalisée**  
 Indique si les fournisseurs de services clients utilisent un magasin de données personnalisé pour le cache local.  Par défaut, ils utilisent le système de fichiers local.  Cette option permet de remplir automatiquement la zone de texte avec une chaîne de connexion par défaut.  Vous pouvez conserver la chaîne de connexion par défaut pour générer automatiquement et utiliser une base de données SQL Server Compact Edition ou spécifier une chaîne de connexion à une base de données SQL Server existante.  Pour plus d'informations, consultez [Comment : configurer les services d'application cliente](../Topic/How%20to:%20Configure%20Client%20Application%20Services.md).  Cette option est désactivée par défaut.  
  
## Voir aussi  
 [Services d'application cliente](../Topic/Client%20Application%20Services.md)   
 [Services, page du Concepteur de projets](../../ide/reference/services-page-project-designer.md)   
 [Comment : configurer les services d'application cliente](../Topic/How%20to:%20Configure%20Client%20Application%20Services.md)   
 [How to: Work Offline with Client Application Services](http://msdn.microsoft.com/fr-fr/f792cb16-8520-4a0f-9dc9-07bfbc454e38)