---
title: Variables de compilation conditionnelle (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, variables
ms.assetid: d6f9827d-c558-412c-8e68-de04c19c3d9d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 900a44dab0ad418cd2899af6423f78016c90fe2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569119"
---
# <a name="conditional-compilation-variables-javascript"></a>Variables de compilation conditionnelle (JavaScript)
Les variables prédéfinies suivantes sont disponibles pour la compilation conditionnelle. Si une variable n’a pas la valeur **true**, elle n’est pas définie et, une fois accessible, se comporte comme `NaN`.  
  
> [!WARNING]
>  La compilation conditionnelle est prise en charge dans toutes les versions d'Internet Explorer antérieures à Internet Explorer 11. À compter du mode standard d'Internet Explorer 11, et des applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], la compilation conditionnelle n'est pas prise en charge.  
  
## <a name="variables"></a>Variables  
  
|Variable|Description|  
|--------------|-----------------|  
|@_win32|True si l'exécution se fait sur un système Win32.|  
|@_win16|True si l'exécution se fait sur un système Win16.|  
|@_mac|True si l'exécution se fait sur un système Apple Macintosh.|  
|@_alpha|True si l'exécution se fait sur un processeur DEC Alpha.|  
|@_x86|True si l'exécution se fait sur un processeur Intel.|  
|@_mc680x0|True si l'exécution se fait sur un processeur Motorola 680x0.|  
|@_PowerPC|True si l'exécution se fait sur un processeur Motorola PowerPC.|  
|@_jscript|Toujours true.|  
|@_jscript_build|Contient le numéro de build du moteur de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
|@_jscript_version|Contient le numéro de version [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] au format major.minor.|