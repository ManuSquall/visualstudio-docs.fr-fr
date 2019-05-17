---
title: IActiveScriptParse32::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fcf11eb2-8e71-4cca-afda-a91791c243ff
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b5a680eea5f5695d3a7253b9cf722af6ebf537c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954884"
---
# <a name="iactivescriptparse32addscriptlet"></a>IActiveScriptParse32::AddScriptlet
Ajoute un scriptlet de code pour le script. Cette méthode est utilisée dans les environnements où l’état permanent du script est étroitement couplé avec le document hôte et l’hôte est chargé pour la restauration du script, plutôt que dans un `IPersist*` interface. Les exemples principales sont des langages de script HTML qui permettent les scriptlets de code incorporé dans le document HTML à joindre aux événements intrinsèques (par exemple, ONCLICK="button1.text='Exit' »).  
  
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
 [in] Adresse d’un nom par défaut à associer le scriptlet. Si le scriptlet ne contient pas d’informations d’affectation de noms (comme dans l’exemple ONCLICK ci-dessus), ce nom sera utilisé pour identifier le scriptlet. Si ce paramètre est `NULL`, le moteur de script fabrique un nom unique, si nécessaire.  
  
 `pstrCode`  
 [in] Adresse du texte de scriptlet à ajouter. L’interprétation de cette chaîne varie selon le langage de script.  
  
 `pstrItemName`  
 [in] Adresse d’une mémoire tampon qui contient le nom de l’élément associé à ce scriptlet. Ce paramètre, en plus de `pstrSubItemName`, identifie l’objet pour lequel le scriptlet est un gestionnaire d’événements.  
  
 `pstrSubItemName`  
 [in] Adresse d’une mémoire tampon qui contient le nom d’un `subobject` de l’élément nommé avec lequel ce scriptlet est associé ; ce nom doit se trouver dans les informations de type de l’élément nommé. Ce paramètre est NULL si le scriptlet doit être associé à l’élément nommé à la place d’un `subitem`. Ce paramètre, en plus de `pstrItemName`, identifie l’objet spécifique pour lequel le scriptlet est un gestionnaire d’événements.  
  
 `pstrEventName`  
 [in] Adresse d’une mémoire tampon qui contient le nom de l’événement pour lequel le scriptlet est un gestionnaire d’événements.  
  
 `pstrDelimiter`  
 [in] Adresse du délimiteur de fin de scriptlet. Lorsque le `pstrCode` paramètre est analysé à partir d’un flux de texte, l’hôte utilise généralement un séparateur, telles que les deux guillemets («), pour détecter la fin du scriptlet. Ce paramètre spécifie le délimiteur utilisé par l’hôte, ce qui permet au moteur de script fournir un prétraitement primitif conditionnel (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le moteur de script utilise ces informations varie selon le moteur de script. Définissez ce paramètre avec la valeur NULL si l’hôte n’utilisez pas un séparateur pour marquer la fin du scriptlet.  
  
 `dwSourceContextCookie`  
 [in] Valeur définie par l’application qui est utilisée pour le débogage.  
  
 `ulStartingLineNumber`  
 [in] Valeur de base zéro qui spécifie la ligne qui commence à l’analyse.  
  
 `dwFlags`  
 [in] Indicateurs associés au scriptlet. Peut être une combinaison des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Indique que le texte du script doit être visible (et, par conséquent, peut être appelé par nom) en tant qu’une méthode globale dans l’espace de noms du script.|  
|SCRIPTTEXT_ISPERSISTENT|Indique que le code ajouté pendant cet appel doit être enregistré si le moteur de script est enregistré (par exemple, via un appel à `IPersist*::Save`), ou si le moteur de script est réinitialisé via une transition vers l’état initialisé. Pour plus d’informations sur cet état, consultez les États de moteur de Script.|  
  
 `pbstrName` ,  
 [out] Nom réel utilisé pour identifier le scriptlet. Elle doit être dans l’ordre de préférence : un nom spécifié explicitement dans le texte de scriptlet, le nom par défaut fourni dans `pstrDefaultName`, ou un nom unique synthétisés par le moteur de script.  
  
 `pexcepinfo` ,  
 [out] Adresse d’une structure contenant des informations sur les exceptions. Cette structure doit être renseignée lorsque DISP_E_EXCEPTION est retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`DISP_E_EXCEPTION`|Une exception s’est produite lors de l’analyse du scriptlet. Le `pexcepinfo` paramètre contient des informations sur l’exception.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_NOTIMPL`|Cette méthode n’est pas pris en charge ; le moteur de script ne prend pas en charge l’ajout des scriptlets de réception d’événements.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé) et par conséquent a échoué.|  
|`OLESCRIPT_E_INVALIDNAME`|Le nom par défaut fourni n’est pas valide dans ce langage de script.|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée s’est produite dans le scriptlet.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)