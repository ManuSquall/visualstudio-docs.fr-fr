---
title: 'Comment : définir des autorisations personnalisées pour une Application ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4003dd1434d55bb43f52ee02801da0f843563456
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077475"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Comment : définir des autorisations personnalisées pour une application ClickOnce
Vous pouvez déployer une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui utilise les autorisations par défaut pour la zone Internet ou Intranet local. Vous pouvez également créer une zone personnalisée pour les autorisations spécifiques nécessaires à l’application. Vous pouvez pour cela personnaliser les autorisations de sécurité dans la page **Sécurité** du **Concepteur de projets**.  
  
### <a name="to-customize-a-permission"></a>Pour personnaliser une autorisation  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Sécurité** .  
  
3.  Cochez la case **Activer les paramètres de sécurité ClickOnce** .  
  
4.  Sélectionnez la case d’option **Il s’agit d’une application de confiance partielle** .  
  
     Les contrôles de la section **Autorisations de sécurité ClickOnce** sont activés.  
  
5.  Dans la liste déroulante **Zone à partir de laquelle votre application sera installée** , cliquez sur **(Personnalisé)**.  
  
6.  Cliquez sur **Modifier les autorisations XML**.  
  
     Le *App.manifest* fichier s’ouvre dans l’éditeur XML.  
  
7.  Avant l’élément `</applicationRequestMinimum>` , ajoutez le code XML pour les autorisations dont votre application a besoin.  
  
    > [!NOTE]
    >  Vous pouvez utiliser la méthode `ToXml` d’un jeu d'autorisations pour générer le code XML du manifeste d’application. Par exemple, pour générer le code XML pour le jeu d’autorisations <xref:System.Security.Permissions.EnvironmentPermission> , appelez la méthode <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> .  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser les Applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
