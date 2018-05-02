---
title: Erreurs du Concepteur de classes
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0af8686af556ca24cdbc9e0a51206f4f0728206
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="additional-information-about-class-designer-errors"></a>Informations supplémentaires sur les erreurs du Concepteur de classes

Le **Concepteur de classes** n’effectue pas le suivi de l’emplacement de vos fichiers sources. Si vous modifiez votre structure de projet ou déplacez des fichiers sources dans votre projet, le **Concepteur de classes** peut donc perdre la trace du type (surtout le type de source d’un typedef, de classes de base ou de types d’associations). Vous pouvez recevoir une erreur telle que **Le Concepteur de classes n’est pas en mesure d’afficher ce type**. Dans ce cas, refaites glisser le code source modifié ou déplacé vers le diagramme de classes pour le réafficher.

## <a name="resources"></a>Ressources

Vous pouvez obtenir de l'aide sur d'autres erreurs et avertissements dans les ressources suivantes :

- [Utilisation du code Visual C++](working-with-visual-cpp-code.md) inclut des informations de dépannage sur l’affichage de C++ dans un diagramme de classes.
- Le [Forum du Concepteur de classes Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754) propose un forum de questions relatives au **Concepteur de classes**.

## <a name="see-also"></a>Voir aussi

- [Conception et affichage des classes et des types](designing-and-viewing-classes-and-types.md)
