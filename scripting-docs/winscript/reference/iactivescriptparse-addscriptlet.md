---
title: IActiveScriptParse::AddScriptlet | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e854ac71dc36263d805160f9336e049856076ce5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724649"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
Ajoute un scriptlet du code pour le script. Cette méthode est utilisée dans les environnements où l’état permanent du script est étroitement avec le document de l’hôte et l’hôte est chargé pour la restauration du script, plutôt que dans un `IPersist*` interface. Les exemples principales sont des langages de script HTML qui autorisent les scriptlets de code incorporé dans le document HTML à attacher aux événements intrinsèques (par exemple, ONCLICK="button1.text='Exit' »).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Adresse d’un nom de valeur par défaut pour associer le scriptlet. Si le scriptlet ne contient pas les informations d’affectation de noms (comme dans l’exemple ONCLICK ci-dessus), ce nom sera utilisé pour identifier le scriptlet. Si ce paramètre est `NULL`, le moteur de script fabrique un nom unique, si nécessaire.  
  
 `pstrCode`  
 [in] Adresse du scriptlet texte à ajouter. L’interprétation de cette chaîne varie selon le langage de script.  
  
 `pstrItemName`  
 [in] Adresse d’une mémoire tampon qui contient le nom de l’élément associé à ce scriptlet. Ce paramètre, en plus de `pstrSubItemName`, identifie l’objet pour lequel le scriptlet est un gestionnaire d’événements.  
  
 `pstrSubItemName`  
 [in] Adresse d’une mémoire tampon qui contient le nom d’un `subobject` de l’élément nommé avec lequel ce scriptlet est associé ; ce nom doit se trouver dans les informations de type de l’élément nommé. Ce paramètre est NULL si le scriptlet doit être associé à l’élément nommé à la place d’un `subitem`. Ce paramètre, en plus de `pstrItemName`, identifie l’objet spécifique pour lequel le scriptlet est un gestionnaire d’événements.  
  
 `pstrEventName`  
 [in] Adresse d’une mémoire tampon qui contient le nom de l’événement pour lequel le scriptlet est un gestionnaire d’événements.  
  
 `pstrDelimiter`  
 [in] Adresse de fin-de-scriptlet délimiteur. Lorsque le `pstrCode` paramètre est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, telles que les guillemets («), pour détecter la fin du scriptlet. Ce paramètre spécifie le délimiteur de l’hôte utilisé, ce qui permet au moteur de script pour fournir certains prétraitement primitifs conditionnelle (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le script permet de moteur dépend de l’utilisation de ces informations sur le moteur de script. Définissez ce paramètre avec la valeur NULL si l’hôte n’utilisez pas un délimiteur pour marquer la fin du scriptlet.  
  
 `dwSourceContextCookie`  
 [in] Valeur définie par l’application qui est utilisée à des fins de débogage.  
  
 `ulStartingLineNumber`  
 [in] Valeur de base zéro qui spécifie la ligne à laquelle l’analyse commencera à.  
  
 `dwFlags`  
 [in] Indicateurs associés le scriptlet. Peut être une combinaison des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Indique que le texte du script doit être visible (et, par conséquent, peut être appelé par nom) en tant qu’une méthode globale dans l’espace de noms du script.|  
|SCRIPTTEXT_ISPERSISTENT|Indique que le code ajouté au cours de cet appel doit être enregistré si le moteur de script est enregistré (par exemple, via un appel à `IPersist*::Save`), ou si le moteur de script est réinitialisé par le biais d’une transition à l’état initialisé. Pour plus d’informations sur cet état, voir les États de moteur de Script.|  
  
 `pbstrName` ,  
 [out] Nom réel utilisé pour identifier le scriptlet. Cela doit être dans l’ordre de préférence : un nom spécifié explicitement dans le texte du scriptlet, le nom par défaut fourni dans `pstrDefaultName`, ou un nom unique synthétisés par le moteur de script.  
  
 `pexcepinfo` ,  
 [out] Adresse d’une structure contenant des informations sur l’exception. Cette structure doit être renseignée lorsque DISP_E_EXCEPTION est retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`DISP_E_EXCEPTION`|Une exception s’est produite lors de l’analyse du scriptlet. Le `pexcepinfo` paramètre contient des informations sur l’exception.|  
|`E_INVALIDARG`|Un argument n’était pas valide.|  
|`E_NOTIMPL`|Cette méthode n’est pas prise en charge ; le moteur de script ne prend pas en charge l’ajout scriptlets de recevoir des événements.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé) et par conséquent a échoué.|  
|`OLESCRIPT_E_INVALIDNAME`|Le nom par défaut fourni n’est pas valide dans ce langage de script.|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée s’est produite dans le scriptlet.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)