---
title: "M&#233;thodes de capture de Graphics Diagnostics | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea21995d-0241-412e-8f62-600c3794247f
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "mithom"
manager: "douge"
---
# M&#233;thodes de capture de Graphics Diagnostics
Insérez l'introduction ici.  
  
## Méthodes de capture  
 Dans [!INCLUDE[win81](../debugger/includes/win81_md.md)], le runtime DirectX 11.2 peut capturer des informations graphiques en interne pour le compte d'outils de débogage comme Graphics Diagnostics. C'est ce que l'on appelle la *capture robuste*.  Avant l'ajout de cette prise en charge au runtime DirectX, la capture des informations graphiques se faisait par l'interception de certains appels de fonction DirectX chargés d'enregistrer des arguments et autres informations avant d'être transférés à DirectX pour y être traités. Il s'agit dans ce cas de *capture héritée*.  
  
 Étant donné que le runtime DirectX est entièrement responsable de la capture d'informations graphiques dans [!INCLUDE[win81](../debugger/includes/win81_md.md)], il n'est pas nécessaire de mettre à jour la capture héritée pour prendre en charge DirectX 11.2. D'ailleurs, la capture héritée est déconseillée.  Cependant, sachant que le runtime DirectX 11.2 ne prend pas en charge les versions de Windows antérieures à [!INCLUDE[win81](../debugger/includes/win81_md.md)], [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] prend toujours en charge la capture héritée pour les applications destinées à [!INCLUDE[win8](../debugger/includes/win8_md.md)] et [!INCLUDE[win7](../debugger/includes/win7_md.md)].  
  
 Les deux méthodes enregistrent des informations similaires et ne modifient pas la façon dont vous capturez les informations graphiques ou utilisez les outils Graphics Diagnostics.  
  
### Capture robuste  
 La capture robuste prend en charge les outils Graphics Diagnostics de [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] sous [!INCLUDE[win81](../debugger/includes/win81_md.md)], [!INCLUDE[winblue_winrt_2](../debugger/includes/winblue_winrt_2_md.md)] et Windows Phone 8.1.  Elle prend en charge DirectX, de la version 10.0 à la version 11.2, et peut capturer des informations graphiques sur les nouvelle fonctionnalités de Direct3D 11.2 \(par exemple, les ressources en mosaïque\).  Cependant, elle ne prend pas entièrement en charge toutes les fonctionnalités de Direct3D 11.2. Par exemple, vous ne pouvez pas déboguer un nuanceur HLSL créé à l'aide de la fonctionnalité de liaison de nuanceur HLSL.  La capture robuste utilise une nouvelle API de capture pour prendre en charge ses scénarios de capture par programmation.  
  
### Capture héritée  
 La capture héritée prend en charge les outils Graphics Diagnostics de [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] et [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] sous [!INCLUDE[win8](../debugger/includes/win8_md.md)], Windows RT 8 et [!INCLUDE[win7](../debugger/includes/win7_md.md)].  Elle prend en charge DirectX, de la version 10.0 à la version 11.1.  La capture héritée ne prend en charge aucune fonctionnalité de Direct3D 11.2 et est déconseillée, sauf pour les scénarios où la capture robuste n'est pas disponible.  La capture héritée utilise l'API de capture définie dans le fichier d'en\-tête `vsgcapture.h` pour prendre en charge ses scénarios de capture par programmation.  Ce type de capture par programmation est aussi déconseillée, sauf pour les scénarios où la capture robuste n'est pas disponible.  
  
## Voir aussi  
 [Capture d'informations Graphics](../debugger/capturing-graphics-information.md)   
 [Procédure pas à pas : capture d'informations Graphics](../debugger/walkthrough-capturing-graphics-information.md)