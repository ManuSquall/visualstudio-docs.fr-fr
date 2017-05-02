---
title: "IActiveScriptParse::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_AddScriptlet"
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::AddScriptlet
Ajoute un scriptlet de code au script.  Cette méthode est utilisée dans les environnements où l'état de persistance du script est entrelacé avec le document hôte et l'hôte est chargé de restaurer le script, plutôt que dans une interface d' `IPersist*` .  Les exemples primaires sont des langages de script HTML qui permettent aux scriptlets de code incorporés dans le document HTML à lier aux événements intrinsèques \(par exemple, ONCLICK\= " button1.text\='Exit »\).  
  
## Syntaxe  
  
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
  
#### Paramètres  
 `pstrDefaultName`  
 \[in\]  Adresse d'un nom par défaut à associer au scriptlet.  Si le scriptlet ne contient pas nommer des informations \(comme dans l'exemple de ONCLICK ci\-dessus\), ce nom est utilisé pour identifier le scriptlet.  Si ce paramètre est `NULL`, le moteur de script fabrique un nom unique, si nécessaire.  
  
 `pstrCode`  
 \[in\]  adresse du texte de scriptlet à ajouter.  La traduction de cette chaîne dépend du langage de script.  
  
 `pstrItemName`  
 \[in\]  L'adresse d'une mémoire tampon qui contient le nom d'élément associé à ce scriptlet.  Ce paramètre, en plus de `pstrSubItemName`, identifie l'objet pour lequel le scriptlet est un gestionnaire d'événements.  
  
 `pstrSubItemName`  
 \[in\]  adresse d'une mémoire tampon qui contient le nom d' `subobject` de l'élément nommé avec lequel ce scriptlet est associé ; ce nom doit être trouvé dans les informations de type d'élément nommé.  Ce paramètre est NULL si le scriptlet doit être associé à l'élément nommé au lieu d' `subitem`.  Ce paramètre, en plus de `pstrItemName`, identifie l'objet spécifique pour lequel le scriptlet est un gestionnaire d'événements.  
  
 `pstrEventName`  
 \[in\]  Adresse d'une mémoire tampon qui contient le nom de l'événement pour lequel le scriptlet est un gestionnaire d'événements.  
  
 `pstrDelimiter`  
 \[in\]  Adresse du délimiteur de fin de scriptlet.  Lorsque le paramètre d' `pstrCode` est analysé d'un flux de texte, l'hôte utilise généralement un séparateur, par exemple deux guillemets simples \('\), pour détecter la fin du scriptlet.  Ce paramètre spécifie que le séparateur qui l'hôte utilisé, ce qui permet au moteur de script pour fournir du prétraitement primitive conditionnel \(par exemple, en remplaçant un guillemet simple \[« \] par deux guillemets simples pour l " utilisation comme séparateur\).  Exactement comment \(et\) si le moteur de script utilise ces informations dépendent du moteur de script.  Définissez ce paramètre POUR ANNULER si l'hôte n'avait pas l'habitude un séparateur pour marquer la fin du scriptlet.  
  
 `dwSourceContextCookie`  
 \[in\]  valeur définie par l'application qui est utilisée à des fins de débogage.  
  
 `ulStartingLineNumber`  
 \[in\]  La valeur de base zéro qui spécifie rayent l'analyse commence à.  
  
 `dwFlags`  
 \[in\]  Balises associées au scriptlet.  Peut être une combinaison des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|SCRIPTTEXT\_ISVISIBLE|Indique que le texte de script doit être visible \(et, par conséquent, être appelé à partir de nom\) comme méthode globale dans l'espace de noms du script.|  
|SCRIPTTEXT\_ISPERSISTENT|Indique que le code ajouté pendant cet appel doit être enregistré si le moteur de script est enregistré \(par exemple, via un appel à `IPersist*::Save`\), ou si le moteur de script est réinitialisé via une transition vers l'état initialisé.  Pour plus d'informations sur ce rapport, consultez les états du moteur de script.|  
  
 `pbstrName` ,  
 \[out\]  nom réel utilisé pour identifier le scriptlet.  Il s'agit d'être dans l'ordre de préférence : un nom spécifié explicitement dans le texte de scriptlet, le nom par défaut fourni dans `pstrDefaultName`, ou un nom unique synthétisé par le moteur de script.  
  
 `pexcepinfo` ,  
 \[out\]  adresse d'une structure contenant les informations sur les exceptions.  Cette structure doit être remplie si DISP\_E\_EXCEPTION est retourné.  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`DISP_E_EXCEPTION`|Une exception s'est produite lors de l'analyse du scriptlet.  Le paramètre d' `pexcepinfo` contient des informations sur l'exception.|  
|`E_INVALIDARG`|Un argument n'était pas valide.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge ; le moteur de script ne prend pas en charge l'ajout de scriptlets de événements descendant.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, le moteur de script n'a pas encore été chargé ou n'a pas été initialisé\) et n'a pas été échoué par conséquent.|  
|`OLESCRIPT_E_INVALIDNAME`|Le nom par défaut fourni est pas valide dans ce langage de script.|  
|`OLESCRIPT_E_SYNTAX`|Une erreur de syntaxe non spécifiée produite dans le scriptlet.|  
  
## Voir aussi  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)