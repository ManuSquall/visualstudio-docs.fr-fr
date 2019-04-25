---
title: 'Procédure : Supprimer les avertissements à l’aide de l’élément de Menu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a8fbc314580b106f5e1e8dae5a0a78d043d3940b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080902"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Procédure : Supprimer des avertissements à l’aide de l’élément de menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
>  Dans la source de suppression n’est pas pris en charge pour les projets de site web.  
  
 Vous pouvez utiliser la fenêtre analyse du Code pour supprimer les avertissements d’analyse du code. Suppression d’un avertissement n’est pas le même que la désactivation. Lorsque vous supprimez un avertissement, elle s’applique uniquement à une instance particulière de la violation. Autres violations de l’avertissement même seront encore signalées dans la fenêtre liste d’erreurs.  
  
 Après avoir exécuté l’analyse du code, vous pouvez déterminer qu’une ou plusieurs des avertissements d’analyse du code qui sont affichent dans la fenêtre analyse du Code ne sont pas applicables à votre application. Par exemple, vous pouvez déterminer que le code est correct en l’état. Ou bien, il peut arriver que certaines violations ont une priorité faible et ne seront pas résolues dans le cycle de développement en cours. Quelle que soit la raison, il est souvent utile indiquer que l’avertissement est non applicable pour informer les membres de votre équipe que le code a été révisé et qu’il a été déterminé que l’avertissement peut être supprimé. Dans la source de suppression est utile, car elle vous permet de placer une suppression proche où l’avertissement est généré.  
  
 Vous pouvez choisir si la suppression s’affichera dans le code source ou dans le fichier de suppression globale. Certaines suppressions doivent être placées dans le fichier de suppression globale. Si c’est le cas, le **dans la Source** option est désactivée.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>Pour supprimer un avertissement à l’aide d’élément de menu  
  
1. Sur le **analyser** menu, choisissez **Windows** , puis **analyse du Code**.  
  
2. Dans le **analyse du Code** fenêtre, sélectionnez le supprimer de l’avertissement.  
  
3. Choisissez les Actions, puis choisissez **supprimer les messages**, puis choisissez **dans la Source** ou **dans le fichier de Suppression de projet**.  
  
     L’avertissement spécifique est supprimé, et l’avertissement s’affiche dans la fenêtre analyse du Code avec un barré.  
  
> [!NOTE]
>  Les suppressions qui n’ont pas de cible apparaissent dans le fichier de suppression globale.
