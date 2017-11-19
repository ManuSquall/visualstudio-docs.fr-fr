---
title: Winrterror, objet (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- WinRTError object [JavaScript]
- JavaScript, WinRTError object
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11b339b4fc3c4bd4f34416ffd98b8f9c3f288f98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="winrterror-object-javascript"></a>WinRTError, objet (JavaScript)
Quand un appel Windows Runtime retourne un HRESULT qui indique une erreur, JavaScript la convertit en erreur Windows Runtime spécifique. Il est disponible uniquement dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], quand le Windows Runtime est disponible, dans l'espace de noms JavaScript globale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
errorObj = new WinRTError();  
  
```  
  
## <a name="remarks"></a>Remarques  
 Le type d'erreur WinRTError est utilisé uniquement pour les erreurs qui proviennent des API Windows Runtime.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment WinRTError est levé et intercepté.  
  
```JavaScript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## <a name="methods"></a>Méthodes  
 L'objet WinRTError n'a pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 L’objet WinRTError a les mêmes propriétés que le [erreur objet](../../javascript/reference/error-object-javascript.md) objet.  
  
## <a name="requirements"></a>Spécifications  
 L'objet WinRTError est pris en charge uniquement dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], et n'est pas pris en charge dans Internet Explorer.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Error](../../javascript/reference/error-object-javascript.md)