---
title: "Comment&#160;: cibler les applications Office via les assemblys PIA (Primary Interop Assembly) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement d'applications (développement Office dans Visual Studio), automatiser"
  - "assemblys (développement Office dans Visual Studio), références d'assemblys PIA (Primary Interop Assembly)"
  - "applications Office (développement Office dans Visual Studio), automatiser"
  - "assemblys PIA (Primary Interop Assembly) Office dans Visual Studio, ajouter des références aux"
  - "assemblys PIA (Primary Interop Assembly) (développement Office dans Visual Studio), ajouter des références aux"
ms.assetid: 9bedae85-32b6-4df6-82b2-9d124fb49636
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Comment&#160;: cibler les applications Office via les assemblys PIA (Primary Interop Assembly)
  Quand vous créez un projet Office, Visual Studio ajoute automatiquement des références aux assemblys PIA \(Primary Interop Assembly\) Microsoft Office qui sont requises pour générer le projet  Vous devez ajouter des références aux autres assemblys PIA dans les scénarios suivants :  
  
-   Vous souhaitez utiliser des fonctionnalités d'autres applications Microsoft Office dans votre projet.  Par exemple, vous pouvez utiliser des fonctionnalités de Microsoft Office Excel dans un projet pour Microsoft Office Word.  
  
-   Vous souhaitez automatiser des applications Microsoft Office qui n'ont pas de projets dédiés dans Visual Studio, comme Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Pour ajouter une référence à un assembly PIA  
  
1.  Ouvrez votre projet Office et sélectionnez le nom du projet dans l'**Explorateur de solutions**.  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter une référence**.  
  
3.  Sous l'onglet **Framework**, sélectionnez l'assembly PIA que vous souhaitez dans la liste **Nom du composant**.  Pour plus d'informations sur les assemblys PIA en Microsoft Office disponibles, consultez [Assemblys PIA &#40;Primary Interop Assembly&#41; Office](../vsto/office-primary-interop-assemblies.md).  
  
     Si le projet cible [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, la valeur **True** est affectée par défaut à la propriété **Incorporer les types interop** pour la référence d'assembly.  Grâce à ce paramètre, votre solution ne requiert pas l'assembly PIA sur les ordinateurs des utilisateurs finaux.  Pour plus d'informations, consultez [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  Dans les projets Office, ajoutez toujours des références aux assemblys PIA Office en utilisant l'onglet **.NET** de la boîte de dialogue **Ajouter une référence** plutôt que l'onglet **COM**.  Pour plus d'informations, consultez [Assemblys PIA &#40;Primary Interop Assembly&#41; Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Cliquez sur **OK**.  
  
     Le nom de l'assembly s'affiche dans le dossier **Références** de l'**Explorateur de solutions**.  
  
## Voir aussi  
 [Assemblys PIA &#40;Primary Interop Assembly&#41; Office](../vsto/office-primary-interop-assemblies.md)   
 [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Développement de solutions Office](../vsto/developing-office-solutions.md)   
 [Comment : installer les assemblys PIA &#40;Primary Interop Assembly&#41; d'Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  