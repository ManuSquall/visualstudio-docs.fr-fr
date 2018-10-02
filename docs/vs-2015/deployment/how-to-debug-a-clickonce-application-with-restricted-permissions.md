---
title: 'Comment : déboguer une Application ClickOnce avec des autorisations restreintes | Microsoft Docs'
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
- debugging [Visual Studio], ClickOnce applications
- ClickOnce deployment, debugging
- ClickOnce applications, debugging
ms.assetid: 6991ea91-5253-451b-923d-22273a3d38b1
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 7733eeefc758f5e5cd6940108ef6ade645893407
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501925"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Comment : déboguer une application ClickOnce avec des autorisations restreintes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : déboguer une Application ClickOnce avec des autorisations restreintes](https://docs.microsoft.com/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions).  
  
En tant que développeur, vous exécutez probablement votre ordinateur de développement avec des autorisations de confiance totale. Vous ne voyez donc pas les mêmes exceptions de sécurité lors du débogage d’une application ClickOnce que celles que l’utilisateur final peut voir quand il l’exécute avec des autorisations restreintes.  
  
 Pour intercepter ces exceptions, vous devez déboguer l’application avec les mêmes autorisations que l’utilisateur final. Le débogage avec des autorisations restreintes peut être activé dans la page **Sécurité** du **Concepteur de projets**.  
  
 De plus, quand vous développez des applications qui appellent des services web, ceux-ci résident souvent sur votre ordinateur de développement. Une fois ces services web déployés, l’utilisateur final y accédera à partir d’une autre URL. Pour émuler l’expérience utilisateur final pendant le débogage, vous pouvez spécifier une URL et le débogueur traitera les services web comme s’ils étaient appelés à partir de cette URL.  
  
### <a name="to-enable-debugging-with-restricted-permissions"></a>Pour activer le débogage avec des autorisations restreintes  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Dans le **Concepteur de projets**, cliquez sur l’onglet **Sécurité** .  
  
3.  Cochez la case **Activer les paramètres de sécurité ClickOnce** , puis cliquez sur la case d’option **Il s’agit d’une application de confiance partielle** .  
  
4.  Cliquez sur le bouton **Avancées** .  
  
5.  Cochez la case **Déboguer cette application à l’aide du jeu d’autorisations sélectionné** , puis cliquez sur **OK**.  
  
     Quand vous déboguez l’application, toute tentative d’accès à une autorisation qui ne fait pas partie du jeu d’autorisations lève une exception de sécurité.  
  
### <a name="to-specify-a-url-for-debugging"></a>Pour spécifier une URL pour le débogage  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Dans le **Concepteur de projets**, cliquez sur l’onglet **Sécurité** .  
  
3.  Cochez la case **Activer les paramètres de sécurité ClickOnce** , puis cliquez sur la case d’option **Il s’agit d’une application de confiance partielle** .  
  
4.  Cliquez sur le bouton **Avancées** .  
  
5.  Cochez la case **Déboguer cette application à l’aide du jeu d’autorisations sélectionné** , puis cliquez sur **OK**.  
  
6.  Dans la zone de texte **Déboguer cette application comme si elle était téléchargée de l’URL suivante** , entrez une URL ou un chemin réseau.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)



