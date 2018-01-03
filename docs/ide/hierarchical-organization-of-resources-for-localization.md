---
title: "Organisation hiérarchique des ressources pour la localisation | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8235f246a52e3f8f53536abdf1aba2c0dede875d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Organisation hiérarchique des ressources pour la localisation
Dans Visual Studio, les ressources localisées (les données comme des chaînes et des images adaptées à chaque culture) sont stockées dans des fichiers distincts et chargées en fonction du paramètre de culture de l’interface utilisateur. Pour comprendre comment les ressources localisées sont chargées, il est utile de les penser selon une organisation hiérarchique.  
  
## <a name="kinds-of-resources-in-the-hierarchy"></a>Types de ressources dans la hiérarchie  
  
-   En haut de la hiérarchie se trouvent les ressources de secours pour votre culture par défaut, par exemple l’anglais (« en »). Ce sont les seules ressources qui n’ont pas leur propre fichier : elles sont stockés dans l’assembly principal.  
  
-   Sous les ressources de secours se trouvent les ressources des cultures neutres. Une culture neutre est associée à une langue, mais pas à un pays/région. Par exemple, Français (« fr ») est une culture neutre. (Notez que les ressources de secours sont également pour une culture neutre, mais une culture spéciale.)  
  
-   En dessous de celles-ci se trouvent les ressources des cultures spécifiques. Une culture spécifique est associée à une langue et à un pays/région. Par exemple, Français (Canada) (« fr-CA ») est une culture spécifique.  
  
 Si une application tente de charger une ressource localisée, comme une chaîne, et ne la trouve pas, elle remonte dans la hiérarchie jusqu’à trouver un fichier de ressources contenant la ressource demandée.  
  
 Le meilleur moyen de stocker vos ressources consiste à les généraliser autant que possible. Cela signifie stocker les chaînes, les images, etc. localisées dans des fichiers de ressources pour des cultures neutres au lieu de cultures spécifiques, chaque fois que c’est possible. Par exemple, si vous avez des ressources pour la culture Français (Belgique) (« fr-BE ») et que les ressources immédiatement au-dessus sont les ressources de secours en anglais, un problème peut se produire quand une personne utilise votre application sur un système configuré pour la culture Français (Canada). Le système recherche un assembly satellite pour « fr-CA », ne le trouve pas et charge l’assembly principal contenant la ressource de secours, qui est Anglais, au lieu de charger les ressources Français. L’image suivante illustre ce scénario non souhaitable.  
  
 ![Ressources spécifiques uniquement](../ide/media/vbspecificresourcesonly.gif "vbSpecificResourcesOnly")  
  
 Si vous suivez la pratique recommandée consistant à placer autant de ressources que possible dans un fichier de ressources neutres pour la culture « fr », l’utilisateur du Français (Canada) ne voit pas les ressources marquées pour la culture « fr-BE », mais par contre voit les chaînes en français. La situation suivante illustre ce scénario préféré.  
  
 ![Graphique NeutralSpecificResources](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")  
  
## <a name="see-also"></a>Voir aussi  
 [Langues des ressources neutres pour la localisation](../ide/neutral-resources-languages-for-localization.md)   
 [Sécurité et assemblys satellites localisés](../ide/security-and-localized-satellite-assemblies.md)   
 [Localisation d’applications](../ide/localizing-applications.md)   
 [Globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md)   
 [Comment : définir la culture et la culture de l’interface utilisateur pour la globalisation des Windows Forms](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0)   
 [Comment : définir la culture et la culture d’interface utilisateur pour la globalisation des pages web ASP.NET](http://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0)