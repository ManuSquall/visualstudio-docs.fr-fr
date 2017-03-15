---
title: "Comment&#160;: supprimer des avertissements &#224; l’aide de l’&#233;l&#233;ment de menu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "avertissements, supprimer"
  - "analyse du code, supprimer les avertissements"
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# Comment&#160;: supprimer des avertissements &#224; l’aide de l’&#233;l&#233;ment de menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Dans la source, la suppression n'est pas prise en charge pour les projets de site Web.  
  
 Vous pouvez utiliser la fenêtre Analyse du Code pour supprimer des avertissements d'analyse du code.  Supprimer un avertissement est différent de sa désactivation.  Lorsque vous supprimez un avertissement, cela s'applique uniquement à une instance particulière de la violation.  Les autres violations du même avertissement seront quand même signalées dans la fenêtre Liste d'erreurs.  
  
 Après avoir exécuté l'analyse du code, vous pouvez déterminer qu'un ou plusieurs des avertissements d'analyse du code affichés dans la fenêtre Analyse du Code ne sont pas applicables à votre application.  Par exemple, vous pouvez déterminer que le code est correct tel qu'il est.  Il se peut également que certaines violations aient une priorité faible et ne soient pas résolues dans le cycle de développement actuel.  Quelle que soit la raison, il est souvent utile d'indiquer que l'avertissement est non applicable pour que les membres de votre équipe sachent que vous avez passé le code en revue et décidé que l'avertissement peut être supprimé.  ISS \(In Source Suppression\) est utile, car il vous permet de placer le code qui supprime un avertissement près de l'emplacement de génération de l'avertissement.  
  
 Vous pouvez choisir si la suppression apparaîtra dans le code source ou dans le fichier de suppression globale.  Certaines suppressions doivent être placées dans le fichier de suppression globale.  Si c'est le cas, l'option **Dans la source** sera désactivée.  
  
### Pour supprimer un avertissement à l'aide d'un élément de menu  
  
1.  Dans le menu **Analyser** , choisissez **Fenêtres** puis choisissez **Analyse du Code**.  
  
2.  Dans la fenêtre **Analyse du Code**, sélectionnez l'avertissement de suppression.  
  
3.  Choisissez des Actions, puis choisissez **Supprimer le\(s\) message\(s\)**, puis choisissez **Dans la source** ou **Dans le fichier de suppression de projet**.  
  
     L'avertissement sélectionné est supprimé, et il apparaît barré dans la fenêtre d'Analyse du Code.  
  
> [!NOTE]
>  Les suppressions qui n'ont pas de cible apparaissent dans le fichier de suppression globale.