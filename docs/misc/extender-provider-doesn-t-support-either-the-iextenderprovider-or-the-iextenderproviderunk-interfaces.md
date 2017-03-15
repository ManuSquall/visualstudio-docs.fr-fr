---
title: "Extender Provider doesn&#39;t support either the IExtenderProvider or the IExtenderProviderUnk interfaces. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_EXT_EXTPROVINVALID"
ms.assetid: 77d596cd-28db-4ad5-bd4d-e451276e869c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Extender Provider doesn&#39;t support either the IExtenderProvider or the IExtenderProviderUnk interfaces.
Le fournisseur d'extendeurs actuellement utilisé ne prend pas en charge l'interface que vous avez implémentée.  
  
### Pour corriger cette erreur  
  
1.  Implémentez IExtenderProvider si l'objet Extendee prend en charge l'interface d'automatisation IDispatch.  
  
     \- ou \-  
  
     Implémentez IExtenderProviderUnk si l'objet Extendee est basé sur IUnknown.  
  
## Voir aussi  
 <xref:EnvDTE.IExtenderProviderUnk>   
 <xref:EnvDTE.IExtenderProvider>   
 <xref:EnvDTE.ObjectExtenders>