---
title: 'Comment : supprimer des avertissements à l’aide de l’élément de menu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96b7433ff4f696989142aa2c2ce47982006b93b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72610015"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Comment : supprimer des avertissements à l’aide de l’élément de menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
> La suppression de la source n’est pas prise en charge pour les projets de site Web.

 Vous pouvez utiliser la fenêtre analyse du code pour supprimer les avertissements d’analyse du code. La suppression d’un avertissement n’est pas la même que la désactivation. Lorsque vous supprimez un avertissement, il s’applique uniquement à une instance particulière de la violation. Les autres violations du même avertissement sont toujours signalées dans la fenêtre de Liste d’erreurs.

 Après avoir exécuté l’analyse du code, vous pouvez déterminer qu’un ou plusieurs des avertissements de l’analyse du code qui sont affichés dans la fenêtre analyse du code ne sont pas applicables à votre application. Par exemple, vous pouvez déterminer que le code est correct comme c’est le cas. Ou peut-être que certaines violations sont de priorité basse et ne seront pas résolues dans le cycle de développement actuel. Quelle que soit la raison, il est souvent utile d’indiquer que l’avertissement n’est pas applicable pour permettre aux membres de votre équipe de savoir que le code a été révisé et qu’il a été déterminé que l’avertissement a pu être supprimé. La suppression de la source est utile, car elle vous permet de mettre fin à la suppression jusqu’à l’endroit où l’avertissement est généré.

 Vous pouvez choisir si la suppression doit s’afficher dans le code source ou dans le fichier de suppression globale. Certaines suppressions doivent être placées dans le fichier de suppression globale. Si c’est le cas, l’option **in source** est désactivée.

### <a name="to-suppress-a-warning-by-using-menu-item"></a>Pour supprimer un avertissement à l’aide d’un élément de menu

1. Dans le menu **analyser** , choisissez **fenêtres** , puis **analyse du code**.

2. Dans la fenêtre **analyse du code** , sélectionnez Supprimer l’avertissement.

3. Choisissez actions, puis supprimer un ou **plusieurs messages**, puis choisissez **dans la source** ou dans le **fichier de suppression du projet**.

     L’avertissement spécifique est supprimé, et l’avertissement apparaît dans la fenêtre analyse du code avec un barré.

> [!NOTE]
> Les suppressions qui n’ont pas de cible apparaissent dans le fichier de suppression globale.
