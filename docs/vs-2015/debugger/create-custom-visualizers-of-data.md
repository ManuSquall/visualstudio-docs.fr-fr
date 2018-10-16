---
title: Créer des visualiseurs de données personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fccaad8cb22bdd5193f2a674c5a9c6bafb49a7a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49217631"
---
# <a name="create-custom-visualizers-of-data"></a>Créer des visualiseurs de données personnalisés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les visualiseurs sont des composants de la [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] interface utilisateur du débogueur. Un *visualiseur* crée une boîte de dialogue ou une autre interface pour afficher une variable ou un objet d’une manière qui convient à son type de données. Par exemple, un visualiseur HTML interprète une chaîne HTML et affiche le résultat tel qu'il apparaîtrait dans une fenêtre du navigateur ; un visualiseur bitmap interprète une structure bitmap et affiche le graphique représenté. Certains visualiseurs vous permettent de modifier et de consulter les données.  
  
 Le débogueur [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] comprend six visualiseurs standard. Il s’agit de texte, les visualiseurs HTML, XML et JSON, qui fonctionnent sur les objets de chaîne ; le visualiseur de l’arborescence WPF, pour afficher les propriétés d’une arborescence d’objets visual WPF ; et le visualiseur dataset, qui fonctionne pour les objets DataSet, DataView et DataTable. Des visualiseurs supplémentaires sont disponibles auprès de tiers et de la communauté. Vous pourrez en télécharger plus tard chez Microsoft Corporation. De plus, vous pouvez écrire vos propres visualiseurs et les installer dans le débogueur [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
> [!NOTE]
>  Dans **Store** applications, seul le texte standard, les visualiseurs HTML, XML et JSON sont pris en charge. Les visualiseurs personnalisés (créés par l'utilisateur) ne sont pas pris en charge.  
  
 Les visualiseurs sont représentés dans le débogueur par une icône de loupe. Lorsque vous voyez l’icône de loupe qui se trouve dans un **DataTip**, dans une fenêtre de variables du débogueur, ou dans le **Espion express** boîte de dialogue, vous pouvez cliquer sur la loupe pour sélectionner un visualiseur approprié au type de données de l’objet correspondant.  
  
 Les visualiseurs ne sont pas pris en charge sur le Compact Framework.  
  
> [!NOTE]
>  Les visualiseurs de débogueur requièrent des privilèges plus importants que ceux octroyés par une application de confiance partielle. Par conséquent, les visualiseurs ne se chargent pas lorsque vous êtes arrêté dans du code à confiance partielle. Pour déboguer à l'aide d'un visualiseur, vous devez exécuter le code avec la confiance totale.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour écrire un visualiseur](../debugger/how-to-write-a-visualizer.md)  
  
 [Procédure pas à pas : écriture d’un visualiseur en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Guide pratique pour installer un visualiseur](../debugger/how-to-install-a-visualizer.md)  
  
 [Guide pratique pour tester et déboguer un visualiseur](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Informations de référence sur l’API du visualiseur](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)



