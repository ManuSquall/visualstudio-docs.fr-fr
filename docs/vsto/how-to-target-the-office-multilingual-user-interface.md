---
title: "Comment&#160;: cibler l&#39;interface utilisateur multilingue d&#39;Office"
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
  - "globalisation (développement Office dans Visual Studio), ciblage de l'interface utilisateur"
  - "localisation (développement Office dans Visual Studio), ciblage de l'interface utilisateur"
  - "MUI (développement Office dans Visual Studio)"
  - "interface utilisateur multilingue (développement Office dans Visual Studio)"
  - "applications Office (développement Office dans Visual Studio), globalisation"
  - "applications Office (développement Office dans Visual Studio), localisation"
ms.assetid: b1f03164-f0cf-42e3-942b-8cf90c242ffb
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Comment&#160;: cibler l&#39;interface utilisateur multilingue d&#39;Office
  L'interface utilisateur multilingue \(MUI, Multilingual User Interface\) est une fonctionnalité de Microsoft Office qui permet à l'utilisateur final de changer la langue de l'interface utilisateur.  Par exemple, un utilisateur final qui travaille avec une interface utilisateur en anglais peut remplacer la langue par l'espagnol.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si votre application doit être utilisée par des personnes qui se servent de plusieurs versions linguistiques d'Office, vous pouvez ajouter le code nécessaire pour modifier automatiquement la langue des chaînes d'interface utilisateur de manière à ce qu'elle corresponde à la langue utilisée par Office sur l'ordinateur de l'utilisateur \(si ce dernier a installé les ressources appropriées\).  
  
### Pour vérifier le paramètre actuel de l'interface utilisateur d'Office  
  
1.  Utilisez la propriété <xref:System.Threading.Thread.CurrentUICulture%2A> du thread actuel.  Configurez la langue de vos chaînes d'interface utilisateur en fonction de celle utilisée par la version d'Office en cours d'exécution sur l'ordinateur de l'utilisateur.  
  
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreCreatingExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/Sheet1.vb#10)]  
  
## Voir aussi  
 [Comment : cibler les applications Office via les assemblys PIA &#40;Primary Interop Assembly&#41;](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md)  
  
  