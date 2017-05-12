---
title: "DateTime et TimeSpan Windows Runtime, repr&#233;sentations | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DateTime (JavaScript)"
  - "JavaScript, dates et heures Windows Runtime"
  - "TimeSpan (JavaScript)"
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# DateTime et TimeSpan Windows Runtime, repr&#233;sentations
La représentation JavaScript des dates et des heures diffère de la version Windows Runtime.  La structure [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) Windows Runtime est représentée en JavaScript en tant que [Date](../javascript/reference/date-object-javascript.md) qui possède un magasin de stockage correspondant aux données `DateTime` \(et qui possède une plage et une précision différentes de l'objet `Date` en JavaScript\).  Si vous modifiez cet objet `Date` personnalisé, il devient un objet `Date` JavaScript standard et perd sa précision.  Les valeurs `Date` en JavaScript peuvent être passées à un objet Windows Runtime `DateTime` et leur plage sera vérifiée, ce qui peut générer des exceptions de marshaling.  
  
 La structure [TimeSpan](http://msdn.microsoft.com/fr-fr/c5defb66-819c-4796-85b5-07ed249a5d86) de Windows Runtime est convertie en millisecondes et retournée sous la forme d'un nombre JavaScript.  
  
## Voir aussi  
 [Utilisation de Windows Runtime dans JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)