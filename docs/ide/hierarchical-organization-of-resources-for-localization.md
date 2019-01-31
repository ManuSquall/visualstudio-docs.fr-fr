---
title: Organisation hiérarchique des ressources pour la localisation
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4df50f1336f235d50d7c897deb2450469f9128b8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038602"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Organisation hiérarchique des ressources pour la localisation

Dans Visual Studio, les ressources localisées (les données comme des chaînes et des images adaptées à chaque culture) sont stockées dans des fichiers distincts et chargées en fonction du paramètre de culture de l’interface utilisateur. Pour comprendre comment les ressources localisées sont chargées, il est utile de les penser selon une organisation hiérarchique.

## <a name="kinds-of-resources-in-the-hierarchy"></a>Types de ressources de la hiérarchie

- En haut de la hiérarchie se trouvent les ressources alternatives de secours pour votre culture par défaut, par exemple l’anglais (« en »). Ce sont les seules ressources qui n’ont pas leur propre fichier : elles sont stockées dans l’assembly principal.

- Sous les ressources de secours se trouvent les ressources des cultures neutres. Une culture neutre est associée à une langue, mais pas à un pays/région. Par exemple, Français (« fr ») est une culture neutre. (Les ressources alternatives de secours sont également pour une culture neutre, mais une culture spéciale.)

- Les ressources pour des cultures spécifiques se trouvent sous les ressources de culture neutre. Une culture spécifique est associée à une langue et à un pays/région. Par exemple, Français (Canada) (« fr-CA ») est une culture spécifique.

Si une application tente de charger une ressource localisée, comme une chaîne, et ne la trouve pas, elle remonte dans la hiérarchie jusqu’à trouver un fichier de ressources contenant la ressource demandée.

Le meilleur moyen de stocker vos ressources consiste à les généraliser autant que possible. Cela signifie stocker les chaînes, les images, etc. localisées dans des fichiers de ressources pour des cultures neutres au lieu de cultures spécifiques, chaque fois que c’est possible. Par exemple, si vous avez des ressources pour la culture Français (Belgique) (« fr-BE ») et que les ressources immédiatement au-dessus sont les ressources de secours en anglais, un problème peut se produire quand une personne utilise votre application sur un système configuré pour la culture Français (Canada). Le système recherche un assembly satellite pour « fr-CA », mais ne le trouve pas : il charge donc l’assembly principal contenant la ressource de secours, qui est « Anglais », au lieu de charger les ressources « Français ». L’image suivante illustre ce scénario non souhaitable.

![Ressources spécifiques uniquement](../ide/media/vbspecificresourcesonly.gif)

Si vous suivez la pratique recommandée consistant à placer autant de ressources que possible dans un fichier de ressources neutres pour la culture « fr », l’utilisateur du Français (Canada) ne voit pas les ressources marquées pour la culture « fr-BE », mais il voit par contre les chaînes en français. La situation suivante illustre ce scénario préféré.

![Graphique NeutralSpecificResources](../ide/media/vbneutralspecificresources.gif)

## <a name="see-also"></a>Voir aussi

- [Langues des ressources neutres pour la localisation](../ide/neutral-resources-languages-for-localization.md)
- [Sécurité et assemblys satellites localisés](../ide/security-and-localized-satellite-assemblies.md)
- [Localiser des applications](../ide/localizing-applications.md)
- [Globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md)