---
title: Compilation conditionnelle (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ConditionalComp_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, overview
- conditional compilation
ms.assetid: a843de4e-3aae-43cd-ad64-477dd00814a2
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d6a5987b21afcab8c62a609dfba33f963d544de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-compilation-javascript"></a>Compilation conditionnelle (JavaScript)
La compilation conditionnelle autorise l'utilisation de nouvelles fonctionnalités de langage de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sans pour autant sacrifier la compatibilité avec les anciennes versions ne les prenant pas en charge.  
  
> [!WARNING]
>  La compilation conditionnelle est prise en charge dans toutes les versions d'Internet Explorer antérieures à Internet Explorer 11. À compter du mode standard d'Internet Explorer 11, et des applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], la compilation conditionnelle n'est pas prise en charge.  
  
## <a name="statements"></a>Instructions  
 La compilation conditionnelle est activée avec l'instruction `@cc_on`, l'instruction `@if` ou encore l'instruction `@set`. Parmi les utilisations types de la compilation conditionnelle, citons l'emploi des nouvelles fonctionnalités de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], l'incorporation du support de débogage à un script et le traçage de l'exécution du code.  
  
 Placez toujours le code de compilation conditionnelle dans des commentaires, afin que les hôtes (comme Netscape Navigator) qui ne prennent pas en charge la compilation conditionnelle l'ignorent. Voici un exemple :  
  
```JavaScript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
 Cet exemple utilise des délimiteurs de commentaires spéciaux qui sont utilisés uniquement si la compilation conditionnelle est activée par l'instruction `@cc_on`. Les moteurs de script qui ne prennent pas en charge la compilation conditionnelle traitent uniquement le message relatif à cette non prise en charge.