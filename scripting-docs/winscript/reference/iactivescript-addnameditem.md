---
title: "IActiveScript::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "AddNamedItem (méthode), IActiveScript (interface)"
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddNamedItem
Ajoute le nom d'un élément racine à l'espace de noms du moteur de script.  Un élément racine est un objet avec des propriétés et des méthodes, une source d'événements, ou les trois.  
  
## Syntaxe  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### Paramètres  
 `pstrName`  
 \[in\]  Adresse d'une mémoire tampon qui contient le nom de l'élément comme affiché du script.  Le nom doit être unique et persistable.  
  
 `dwFlags`  
 \[in\]  Balises associées à un élément.  Peut être une combinaison de ces valeurs :  
  
|Valeur|Signification|  
|------------|-------------------|  
|SCRIPTITEM\_CODEONLY|Indique que l'élément nommé représente un objet code code, et que l'hôte n'a aucun `IUnknown` à associer à cet objet code code.  L'hôte possède un seul nom de cet objet.  Dans les langages orientés objets tels que C\+\+, cette balise créerait une classe.  Tous les langages prennent en charge cette balise.|  
|SCRIPTITEM\_GLOBALMEMBERS|Indique que l'élément est une collection de propriétés globales et de méthodes associées au script.  Normalement, un moteur de script ignorerait le nom de l'objet \(autre que pour les besoins de l'utiliser comme cookie pour la méthode d' [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) , ou pour résoudre la portée explicite\) et exposerait ses membres en tant que variables globales et méthodes.  Cela permet à l'hôte pour étendre la bibliothèque \(fonctions runtime etc.\) disponible pour un script.  Il est autorisé au moteur de script pour gérer des conflits de noms \(par exemple, lorsque deux éléments de SCRIPTITEM\_GLOBALMEMBERS ont des méthodes du même nom\), bien qu'une erreur ne doit pas être retournée à cause de cette situation.|  
|SCRIPTITEM\_ISPERSISTENT|Indique que l'élément doit être enregistré si le moteur de script est enregistré.  De même, la définition de cette balise indique qu'une transition vers l'état initialisé doit conserver le nom de l'élément et les informations de type \(le moteur de script doit, toutefois, libérer tous les pointeurs vers des interfaces de l'objet réel.\)|  
|SCRIPTITEM\_ISSOURCE|Indique que les événements de sources d'élément que le script peut défiler.  Les objets enfants \(propriétés de l'objet ayant eux\-mêmes des objets\) peuvent également des événements de source au script.  Ce n'est pas récurrente, mais il fournit un mécanisme commode pour le cas courant, par exemple, pour créer un conteneur et tous ses contrôles membres.|  
|SCRIPTITEM\_ISVISIBLE|Indique que le nom de l'élément est disponible dans l'espace de noms du script, ce qui permet l'accès aux propriétés, les méthodes, et de l'élément.  Par convention les propriétés de l'élément incluent les enfants de l'élément ; par conséquent, toutes les propriétés de l'objet enfant et méthodes \(et leurs enfants, de manière récursive\) seront accessibles.|  
|SCRIPTITEM\_NOCODE|Indique que l'élément est simplement un nom ajouté à l'espace de noms du script, et ne doit pas être traité comme un élément dont le code doit être associé.  Par exemple, sans cette balise est définie, VBScript crée un module distinct pour l'élément nommé, et C\+\+ peut créer une classe wrapper distincte pour l'élément nommé.|  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`E_INVALIDARG`|Un argument n'était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, le moteur de script n'a pas encore été chargé ou n'a pas été initialisé.\)|  
  
## Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)