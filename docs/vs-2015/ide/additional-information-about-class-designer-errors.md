---
title: Informations supplémentaires sur les erreurs du Concepteur de classes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a095cd909dcd4d378fddc91c9151cf28e34a8ee5
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852206"
---
# <a name="additional-information-about-class-designer-errors"></a>Informations supplémentaires sur les erreurs du Concepteur de classes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le Concepteur de classes n'effectue pas le suivi de l'emplacement de vos fichiers sources ; par conséquent, si vous modifiez votre structure de projet ou si vous déplacez des fichiers sources dans votre projet, le Concepteur de classes peut perdre la trace du type (surtout le type de source d'un typedef, de classes de base ou de types d'associations). Vous pouvez recevoir une erreur telle que **Le Concepteur de classes n’est pas en mesure d’afficher ce type**. Dans ce cas, refaites glisser le code source modifié ou déplacé vers le diagramme de classes pour le réafficher.

 Vous pouvez obtenir de l'aide sur d'autres erreurs et avertissements dans les ressources suivantes :

 [L’utilisation du C++ code Visual (Concepteur de classes)](../ide/working-with-visual-cpp-code-class-designer.md) comprend des informations de C++ dépannage sur l’affichage dans un diagramme de classes.

 Le [Forum du Concepteur de classes Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vsclassdesigner/threads?page=1) propose un forum de questions relatives au Concepteur de classes.

## <a name="see-also"></a>Voir aussi
 [Conception et affichage des classes et des types](../ide/designing-and-viewing-classes-and-types.md)
