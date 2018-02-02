---
title: "Comment : supprimer les avertissements à l’aide de l’élément de Menu | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5ce2369b5b97f1767a17686d3de2d4127150c05d
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2018
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Comment : supprimer des avertissements à l’aide de l’élément de menu
> [!NOTE]
>  Dans la source de suppression n’est pas prise en charge pour les projets de site web.  
  
 Vous pouvez utiliser la fenêtre analyse du Code pour supprimer les avertissements d’analyse du code. Suppression d’un avertissement n’est pas le même que la désactivation. Lorsque vous supprimez un avertissement, elle s’applique uniquement à une instance particulière de la violation. Autres violations du même avertissement seront toujours signalées dans la fenêtre liste d’erreurs.  
  
 Après avoir exécuté l’analyse du code, vous pouvez déterminer qu’un ou plusieurs des avertissements d’analyse du code qui sont affichent dans la fenêtre analyse du Code ne sont pas applicables à votre application. Par exemple, vous pouvez déterminer que le code est correct tel quel. Ou bien, il peut être le cas que certaines violations ont une priorité faible et ne doit pas être résolues dans le cycle de développement actuel. Quelle que soit la raison, il est souvent utile d’indiquer que l’avertissement est non applicable pour informer les membres de votre équipe que le code a été révisé et qu’il a été déterminé que l’avertissement peut être supprimé. Dans la source de suppression est utile car elle vous permet de placer une suppression proche où l’avertissement est généré.  
  
 Vous pouvez choisir si la suppression s’affichera dans le code source ou dans le fichier de suppression globale. Certaines suppressions doivent être placées dans le fichier de suppression globale. Si c’est le cas, le **dans la Source** option est désactivée.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>Pour supprimer un avertissement à l’aide d’élément de menu  
  
1.  Sur le **analyser** menu, choisissez **Windows** , puis **l’analyse du Code**.  
  
2.  Dans le **l’analyse du Code** fenêtre, sélectionnez le supprimer de l’avertissement.  
  
3.  Choisissez les Actions, puis choisissez **supprimer les messages**, puis choisissez **dans la Source** ou **dans le fichier de Suppression de projet**.  
  
     L’avertissement spécifique est supprimé, et l’avertissement s’affiche dans la fenêtre analyse du Code barré.  
  
> [!NOTE]
>  Les suppressions qui n’ont pas de cible apparaissent dans le fichier de suppression globale.