---
title: 'IActiveScriptParse :: AddScriptlet | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_AddScriptlet
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1b4ac460afea1efd538c64224d84afef49d1a67
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573539"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
Ajoute un scriptlet de code au script. Cette méthode est utilisée dans les environnements où l’état persistant du script est entrelacé avec le document hôte et où l’hôte est responsable de la restauration du script, plutôt que via une interface `IPersist*`. Les exemples principaux sont des langages de script HTML qui permettent aux scriptlets de code incorporé dans le document HTML d’être attachés à des événements intrinsèques (par exemple, ONCLICK = "Button1. Text = 'Exit'»).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrDefaultName`  
 dans Adresse d’un nom par défaut à associer au scriptlet. Si le scriptlet ne contient pas d’informations de nommage (comme dans l’exemple ONCLICK ci-dessus), ce nom sera utilisé pour identifier le scriptlet. Si ce paramètre est `NULL`, le moteur de script fabrique un nom unique, si nécessaire.  
  
 `pstrCode`  
 dans Adresse du texte scriptlet à ajouter. L’interprétation de cette chaîne dépend du langage de script.  
  
 `pstrItemName`  
 dans Adresse d’une mémoire tampon qui contient le nom d’élément associé à ce scriptlet. Ce paramètre, en plus de `pstrSubItemName`, identifie l’objet pour lequel le scriptlet est un gestionnaire d’événements.  
  
 `pstrSubItemName`  
 dans Adresse d’une mémoire tampon qui contient le nom d’un `subobject` de l’élément nommé auquel ce scriptlet est associé ; ce nom doit se trouver dans les informations de type de l’élément nommé. Ce paramètre a la valeur NULL si le scriptlet doit être associé à l’élément nommé et non à un `subitem`. Ce paramètre, en plus de `pstrItemName`, identifie l’objet spécifique pour lequel le scriptlet est un gestionnaire d’événements.  
  
 `pstrEventName`  
 dans Adresse d’une mémoire tampon qui contient le nom de l’événement pour lequel le scriptlet est un gestionnaire d’événements.  
  
 `pstrDelimiter`  
 dans Adresse du délimiteur de fin de scriptlet. Lorsque le paramètre `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, tel que deux guillemets simples (' '), pour détecter la fin du scriptlet. Ce paramètre spécifie le délimiteur utilisé par l’hôte, ce qui permet au moteur de script de fournir un prétraitement de primitive conditionnelle (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). La façon dont (et si) le moteur de script utilise ces informations dépend du moteur de script. Affectez la valeur NULL à ce paramètre si l’hôte n’a pas utilisé de délimiteur pour marquer la fin du scriptlet.  
  
 `dwSourceContextCookie`  
 dans Valeur définie par l’application qui est utilisée à des fins de débogage.  
  
 `ulStartingLineNumber`  
 dans Valeur de base zéro qui spécifie la ligne à laquelle l’analyse doit commencer.  
  
 `dwFlags`  
 dans Indicateurs associés au scriptlet. Peut être une combinaison des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Indique que le texte du script doit être visible (et, par conséquent, peut être appelé par son nom) en tant que méthode globale dans l’espace de noms du script.|  
|SCRIPTTEXT_ISPERSISTENT|Indique que le code ajouté au cours de cet appel doit être enregistré en cas d’enregistrement du moteur de script (par exemple, via un appel à `IPersist*::Save`), ou si le moteur de script est réinitialisé au moyen d’une transition vers l’état initialisé. Pour plus d’informations sur cet État, consultez États du moteur de script.|  
  
 `pbstrName` ,  
 à Nom réel utilisé pour identifier le scriptlet. Elle doit être triée par ordre de préférence : un nom spécifié explicitement dans le scriptlet Text, le nom par défaut fourni dans `pstrDefaultName` ou un nom unique synthétisé par le moteur de script.  
  
 `pexcepinfo` ,  
 à Adresse d’une structure contenant des informations sur les exceptions. Cette structure doit être remplie si DISP_E_EXCEPTION est retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`DISP_E_EXCEPTION`|Une exception s’est produite lors de l’analyse du scriptlet. Le paramètre `pexcepinfo` contient des informations sur l’exception.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_NOTIMPL`|Cette méthode n’est pas prise en charge. le moteur de script ne prend pas en charge l’ajout de scriptlets de réception d’événements.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n’a pas encore été chargé ou initialisé) et par conséquent a échoué.|  
|`OLESCRIPT_E_INVALIDNAME`|Le nom par défaut fourni n’est pas valide dans ce langage de script.|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée s’est produite dans le scriptlet.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)