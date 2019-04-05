---
title: Ajout d’Extensions à des définitions DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd45a2345e6e5b28b74cb27fac226514c3f92a04
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948643"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Ajout d'extensions à des définitions DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extension de définition DSL vous permet de créer un package d’extensions à un langage spécifique à un domaine (DSL). L’extension DSL, qui est contenue dans une Extension d’intégration Visual Studio (VSIX), peut être installée sur l’ordinateur d’un utilisateur dans la même manière qu’une solution DSL. Les fonctionnalités supplémentaires peuvent être dynamiquement activées et désactivées au moment de l’exécution. DSL n’ont pas à être explicitement conçu pour l’extension, et extensions peuvent être conçues par des tiers ou ultérieurement sans en altérer le DSL étendue.  
  
 Les fonctionnalités supplémentaires peuvent être les suivants :  
  
- Propriétés des éléments de modèle et de présentation  
  
- Éléments décoratifs pour les formes et connecteurs  
  
- Classes, les relations, formes et connecteurs  
  
- Contraintes de validation  
  
- Onglets et des éléments de boîte à outils  
  
  Un utilisateur d’un langage DSL étendu peut créer et enregistrer un modèle qui contient les instances des fonctionnalités supplémentaires, et ils peuvent être lus par d’autres utilisateurs qui ont installé l’extension appropriée. Les utilisateurs qui n’ont pas installé l’extension ne peut pas utiliser les fonctionnalités supplémentaires, mais ils peuvent mettre à jour et enregistrer un modèle sans perdre les fonctionnalités supplémentaires.  
  
  Pour plus d’exemples de code et plus d’informations sur cette fonctionnalité, consultez le [Visual Studio Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128) site Web.  
  
## <a name="see-also"></a>Voir aussi  
 [Visual Studio Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)
