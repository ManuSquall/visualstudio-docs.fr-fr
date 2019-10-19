---
title: 'IActiveScript :: AddNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a343e38b944ca36da221da39832046c19b332230
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575827"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Ajoute le nom d’un élément de niveau racine à l’espace de noms du moteur de script. Un élément de niveau racine est un objet avec des propriétés et des méthodes, une source d’événement ou les trois.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrName`  
 dans Adresse d’une mémoire tampon qui contient le nom de l’élément tel qu’il est affiché à partir du script. Le nom doit être unique et persistant.  
  
 `dwFlags`  
 dans Indicateurs associés à un élément. Peut être une combinaison de ces valeurs :  
  
|valeur|Signification|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Indique que l’élément nommé représente un objet de code uniquement, et que l’hôte n’a aucun `IUnknown` à associer à cet objet de code uniquement. L’hôte a uniquement un nom pour cet objet. Dans les langages orientés objet C++tels que, cet indicateur crée une classe. Tous les langages ne prennent pas en charge cet indicateur.|  
|SCRIPTITEM_GLOBALMEMBERS|Indique que l’élément est une collection de propriétés et de méthodes globales associées au script. Normalement, un moteur de script ignore le nom de l’objet (autre que dans le but de l’utiliser comme cookie pour la méthode [IActiveScriptSite :: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) , ou pour la résolution de l’étendue explicite) et expose ses membres en tant que méthodes et variables globales. Cela permet à l’hôte d’étendre la bibliothèque (fonctions runtime, etc.) disponibles pour le script. Il est laissé au moteur de script de traiter les conflits de noms (par exemple, lorsque deux éléments SCRIPTITEM_GLOBALMEMBERS ont des méthodes du même nom), bien qu’une erreur ne soit pas retournée en raison de cette situation.|  
|SCRIPTITEM_ISPERSISTENT|Indique que l’élément doit être enregistré si le moteur de script est enregistré. De même, la définition de cet indicateur indique qu’une transition vers l’état initialisé doit conserver le nom et les informations de type de l’élément (le moteur de script doit cependant libérer tous les pointeurs vers les interfaces sur l’objet réel).|  
|SCRIPTITEM_ISSOURCE|Indique que les événements de sources d’élément que le script peut recevoir. Les objets enfants (propriétés de l’objet qui sont eux-mêmes objets) peuvent également générer des événements source pour le script. Ce n’est pas récursif, mais il fournit un mécanisme commode pour le cas courant, par exemple, pour créer un conteneur et tous ses contrôles membres.|  
|SCRIPTITEM_ISVISIBLE|Indique que le nom de l’élément est disponible dans l’espace de noms du script, ce qui permet d’accéder aux propriétés, méthodes et événements de l’élément. Par Convention, les propriétés de l’élément incluent les enfants de l’élément ; par conséquent, toutes les propriétés et méthodes de l’objet enfant (et leurs enfants, de manière récursive) sont accessibles.|  
|SCRIPTITEM_NOCODE|Indique que l’élément est simplement un nom qui est ajouté à l’espace de noms du script et qu’il ne doit pas être traité comme un élément pour lequel du code doit être associé. Par exemple, si cet indicateur n’est pas défini, VBScript crée un module séparé pour l’élément nommé et C++ peut créer une classe wrapper distincte pour l’élément nommé.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n’a pas encore été chargé ou initialisé).|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)