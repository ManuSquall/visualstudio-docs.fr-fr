---
title: "Ensemble de r&#232;gles des r&#232;gles minimales manag&#233;es pour le code manag&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 2
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 2
---
# Ensemble de r&#232;gles des r&#232;gles minimales manag&#233;es pour le code manag&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les Règles Minimales Managées sont focalisées sur les problèmes les plus critiques présents dans votre code, comme les failles de sécurité éventuelles, les arrêts brutaux des applications et autres erreurs de logique ou de conception importantes.  Incluez cet ensemble de règles dans tous les ensembles de règles personnalisés que vous créez pour vos projets.  
  
|Règle|Description|  
|-----------|-----------------|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|Les types qui possèdent des champs supprimables doivent être supprimables|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Supprimer les finaliseurs vides|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Les champs pouvant être supprimés doivent l'être|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Surcharger l'opérateur égal \(equals\) en surchargeant ValueType.Equals|