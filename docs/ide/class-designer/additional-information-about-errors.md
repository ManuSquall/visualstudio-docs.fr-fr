---
title: Erreurs du Concepteur de classes
ms.date: 11/04/2016
ms.topic: troubleshooting
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
- error messages, class diagrams
- Class Designer [Visual Studio], errors
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2fe684f4b10e3570e96a88c34d1e1c08c7388da
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631909"
---
# <a name="class-designer-errors"></a>Erreurs du Concepteur de classes

Le **Concepteur de classes** n’effectue pas le suivi de l’emplacement de vos fichiers sources. Si vous modifiez votre structure de projet ou déplacez des fichiers sources dans le projet, le **Concepteur de classes** peut perdre la trace du type. Par exemple, il est fréquent de modifier le type source d’un typedef, de classes de base et de types d’associations. Vous pouvez recevoir une erreur telle que **Le Concepteur de classes n’est pas en mesure d’afficher ce type**. Pour résoudre cette erreur, refaites glisser le code source modifié ou déplacé vers le diagramme de classes pour l’afficher.

## <a name="resources"></a>Ressources

Vous pouvez obtenir de l'aide sur d'autres erreurs et avertissements dans les ressources suivantes :

- [Utiliser le code Visual C++](working-with-visual-cpp-code.md) inclut des informations de dépannage sur l’affichage de C++ dans un diagramme de classes.
- Le [Forum du Concepteur de classes Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754) propose un forum de questions relatives au **Concepteur de classes**.

## <a name="see-also"></a>Voir aussi

- [Concevoir et afficher des classes et des types](designing-and-viewing-classes-and-types.md)
