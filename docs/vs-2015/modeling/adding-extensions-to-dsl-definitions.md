---
title: Ajout d’extensions aux définitions DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 447001a8aefa22fe15bce9158eddeb0cdb26e4e8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654717"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Ajout d'extensions à des définitions DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’extension de définition DSL vous permet de créer un package d’extensions dans un langage spécifique à un domaine (DSL). L’extension DSL, qui est contenue dans une extension d’intégration Visual Studio (VSIX), peut être installée sur l’ordinateur d’un utilisateur de la même manière qu’une solution DSL. Les fonctionnalités supplémentaires peuvent être activées et désactivées de manière dynamique au moment de l’exécution. Les DSL n’ont pas besoin d’être explicitement conçus pour l’extension, et les extensions peuvent être conçues ultérieurement ou par des tiers sans modifier le DSL étendu.

 Les fonctionnalités supplémentaires peuvent inclure les éléments suivants :

- Propriétés des éléments de modèle et de présentation

- Éléments décoratifs pour les formes et les connecteurs

- Classes, relations, formes et connecteurs

- Contraintes de validation

- Onglets et éléments de boîte à outils

  Un utilisateur d’un DSL étendu peut créer et enregistrer un modèle qui contient des instances des fonctionnalités supplémentaires, et celles-ci peuvent être lues par d’autres utilisateurs qui ont installé l’extension appropriée. Les utilisateurs qui n’ont pas installé l’extension ne peuvent pas utiliser les fonctionnalités supplémentaires, mais ils peuvent mettre à jour et enregistrer un modèle sans perdre les fonctionnalités supplémentaires.

  Pour obtenir un exemple de code et des informations supplémentaires sur cette fonctionnalité, consultez le site Web du [Kit de développement logiciel de visualisation et de modélisation de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=186128) .

## <a name="see-also"></a>Voir aussi
 [Kit de développement logiciel de visualisation et de modélisation Visual Studio](http://go.microsoft.com/fwlink/?LinkID=186128)
