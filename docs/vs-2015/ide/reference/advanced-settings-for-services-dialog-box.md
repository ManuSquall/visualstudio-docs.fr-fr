---
title: Paramètres avancés pour les services, boîte de dialogue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4a7affd12dceeb8802740b7d0cd502ede051f5ad
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779134"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Paramètres avancés pour les services, boîte de dialogue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Les services d’application cliente fournissent un accès simplifié aux services de connexion, de rôles et de profil [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] à partir des applications Windows Forms et WPF (Windows Presentation Foundation). Vous pouvez utiliser la page **Services** du **Concepteur de projet** pour configurer les services d’application cliente. Pour plus d’informations sur la page **Services**, consultez [Services, page du Concepteur de projet](../../ide/reference/services-page-project-designer.md).  
  
 Utilisez la boîte de dialogue **Paramètres avancés pour les services** de la page **Services** dans le **Concepteur de projet** pour configurer les paramètres avancés des services d’application cliente. Ces paramètres vous permettent de remplacer certains comportements de service d’application par défaut pour activer des scénarios moins courants. Pour plus d’informations, consultez [Services d’application cliente](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).  
  
 Pour accéder à la boîte de dialogue **Paramètres avancés pour les services**, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Quand le **Concepteur de projet** s’affiche, cliquez sur l’onglet **Services**, puis sur le bouton **Avancé**. Ce bouton est désactivé tant que vous n’activez pas les services d’application cliente.  
  
## <a name="task-list"></a>Liste des tâches  
 [Comment : configurer les services d’application cliente](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)  
  
 [Guide pratique pour Travailler hors connexion avec les Services d’Application cliente](http://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Enregistrer le hachage de mot de passe localement pour activer la connexion hors connexion**  
 Indique si le mot de passe de l’utilisateur sera mis en cache localement sous une forme chiffrée pour permettre à l’utilisateur de se connecter quand l’application est en mode hors connexion. Pour plus d'informations, voir [Procédure : Travailler hors connexion avec les Services d’Application cliente](http://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38). Cette option est activée par défaut.  
  
 **Imposer aux utilisateurs de se reconnecter chaque fois que le cookie du serveur expire**  
 Indique si des utilisateurs précédemment authentifiés font l’objet d’une nouvelle authentification automatique quand votre application accède aux service de rôles ou de profil et que le cookie d’authentification du serveur a expiré. Sélectionnez cette option pour refuser l’accès aux services d’application et exiger une nouvelle authentification après l’expiration du cookie. Elle est utile pour les applications déployées dans des emplacements publics afin de garantir que les utilisateurs qui quittent l’application en cours d’exécution ne restent pas authentifiés indéfiniment. Cette option est désactivée par défaut.  
  
 **Dépassement du délai de cache du service de rôle**  
 Indique la durée pendant laquelle le fournisseur de rôles clients utilisera les valeurs de rôle mises en cache au lieu d’accéder au service de rôles. Choisissez une valeur peu élevée quand les rôles sont fréquemment mis à jour ou une valeur plus élevée quand ils sont rarement mis à jour. La valeur par défaut est un jour.  
  
 Le fournisseur de rôles accède aux valeurs de rôle mises en cache ou au service de rôles quand vous appelez la méthode <xref:System.Web.Security.RolePrincipal.IsInRole%2A>. Pour effacer le cache par programmation et forcer cette méthode afin d’accéder au service distant, appelez la méthode <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>.  
  
 **Utiliser la chaîne de connexion personnalisée**  
 Indique si les fournisseurs de services clients utilisent un magasin de données personnalisé pour le cache local. Par défaut, ils utilisent le système de fichiers local. Quand elle est sélectionnée, cette option permet de remplir automatiquement la zone de texte avec une chaîne de connexion par défaut. Vous pouvez conserver la chaîne de connexion par défaut pour automatiquement générer et utiliser une base de données SQL Server Compact Edition. Vous pouvez également spécifier une chaîne de connexion à une base de données SQL Server existante. Pour plus d'informations, consultez [How to: Configure Client Application Services](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8). Cette option est désactivée par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [Services d’application cliente](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e)   
 [Services, page du Concepteur de projet](../../ide/reference/services-page-project-designer.md)   
 [Comment : configurer les services d’application cliente](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)   
 [Guide pratique pour Travailler hors connexion avec les Services d’Application cliente](http://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)
