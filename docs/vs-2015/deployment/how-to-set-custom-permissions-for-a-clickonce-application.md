---
title: 'Comment : définir des autorisations personnalisées pour une Application ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 6cf4b1c91650bf505daececfdf46ba42cfee68fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504384"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Comment : définir des autorisations personnalisées pour une application ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : Set Custom Permissions for a ClickOnce Application](https://docs.microsoft.com/visualstudio/deployment/how-to-set-custom-permissions-for-a-clickonce-application).  
  
Vous pouvez déployer une application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] qui utilise les autorisations par défaut pour la zone Internet ou Intranet local. Vous pouvez également créer une zone personnalisée pour les autorisations spécifiques nécessaires à l’application. Vous pouvez pour cela personnaliser les autorisations de sécurité dans la page **Sécurité** du **Concepteur de projets**.  
  
### <a name="to-customize-a-permission"></a>Pour personnaliser une autorisation  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Sécurité** .  
  
3.  Cochez la case **Activer les paramètres de sécurité ClickOnce** .  
  
4.  Sélectionnez la case d’option **Il s’agit d’une application de confiance partielle** .  
  
     Les contrôles de la section **Autorisations de sécurité ClickOnce** sont activés.  
  
5.  Dans la liste déroulante **Zone à partir de laquelle votre application sera installée** , cliquez sur **(Personnalisé)**.  
  
6.  Cliquez sur **Modifier les autorisations XML**.  
  
     Le fichier app.manifest s’ouvre dans l’éditeur XML.  
  
7.  Avant l’élément `</applicationRequestMinimum>` , ajoutez le code XML pour les autorisations dont votre application a besoin.  
  
    > [!NOTE]
    >  Vous pouvez utiliser la méthode `ToXml` d’un jeu d'autorisations pour générer le code XML du manifeste d’application. Par exemple, pour générer le code XML pour le jeu d’autorisations <xref:System.Security.Permissions.EnvironmentPermission> , appelez la méthode <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> . Pour plus d’informations sur la structure du code XML de jeu d’autorisations, consultez [NIB: Comment : importer un jeu d’autorisations à l’aide d’un fichier XML](http://msdn.microsoft.com/en-us/dea16b54-c108-408a-ac36-cdc05f746236).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)



