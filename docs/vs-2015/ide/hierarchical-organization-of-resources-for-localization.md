---
title: Organisation hiérarchique des ressources pour la localisation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: baa86408ca681d65266cb5dae3fe2bf9fca8f97c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62584588"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Organisation hiérarchique des ressources pour la localisation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, les ressources localisées (les données comme des chaînes et des images adaptées à chaque culture) sont stockées dans des fichiers distincts et chargées en fonction du paramètre de culture de l’interface utilisateur. Pour comprendre comment les ressources localisées sont chargées, il est utile de les penser selon une organisation hiérarchique.  
  
## <a name="kinds-of-resources-in-the-hierarchy"></a>Types de ressources dans la hiérarchie  
  
- En haut de la hiérarchie se trouvent les ressources de secours pour votre culture par défaut, par exemple l’anglais (« en »). Ce sont les seules ressources qui n’ont pas leur propre fichier : elles sont stockés dans l’assembly principal.  
  
- Sous les ressources de secours se trouvent les ressources des cultures neutres. Une culture neutre est associée à une langue, mais pas à un pays/région. Par exemple, Français (« fr ») est une culture neutre. (Notez que les ressources de secours sont également pour une culture neutre, mais une culture spéciale.)  
  
- En dessous de celles-ci se trouvent les ressources des cultures spécifiques. Une culture spécifique est associée à une langue et à un pays/région. Par exemple, Français (Canada) (« fr-CA ») est une culture spécifique.  
  
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
 [Guide pratique pour Définir la Culture et la Culture d’interface utilisateur pour la globalisation des Windows Forms](http://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0)   
 [Guide pratique pour Définir la Culture et la Culture d’interface utilisateur pour la globalisation des pages Web ASP.NET](http://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0)
