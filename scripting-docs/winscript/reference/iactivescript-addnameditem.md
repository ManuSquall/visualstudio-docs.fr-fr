---
title: IActiveScript::AddNamedItem | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4ae4a84821d0db226cbecb01e329e4f2941a675d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095093"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Ajoute le nom d’un élément de niveau racine pour l’espace de noms du moteur de script. Un élément de niveau racine est un objet avec les propriétés et méthodes, une source d’événement ou tous les trois.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrName`  
 [in] Adresse d’une mémoire tampon qui contient le nom de l’élément tel qu’affiché à partir du script. Le nom doit être unique et persistante.  
  
 `dwFlags`  
 [in] Indicateurs associés à un élément. Peut être une combinaison des valeurs suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Indique que l’élément nommé représente un objet de code uniquement, et que l’hôte n’a aucun `IUnknown` à associer à cet objet de code uniquement. L’hôte a seulement un nom pour cet objet. Dans les langages orientés objet tels que C++, cet indicateur créerait une classe. Tous les langages ne prennent en charge cet indicateur.|  
|SCRIPTITEM_GLOBALMEMBERS|Indique que l’élément est une collection de propriétés globales et de méthodes associés au script. Normalement, un moteur de script ignore le nom d’objet (autre que pour les besoins de l’utiliser comme un cookie pour le [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) (méthode), ou la résolution de portée explicite) et exposer ses membres comme global les variables et méthodes. Cela permet à l’hôte étendre la bibliothèque (fonctions d’exécution et ainsi de suite) disponible pour le script. Il est laissé au moteur de script à traiter avec le nom est en conflit (par exemple, lorsque deux éléments SCRIPTITEM_GLOBALMEMBERS proposent des méthodes du même nom), même si une erreur ne doit pas être retournée en raison de cette situation.|  
|SCRIPTITEM_ISPERSISTENT|Indique que l’élément doit être enregistré si le moteur de script est enregistré. De même, la définition de cet indicateur indique qu’une transition vers l’état initialisé doit conserver nom et le type d’informations de l’élément (le moteur de script doit, cependant, libérer tous les pointeurs vers les interfaces sur l’objet réel).|  
|SCRIPTITEM_ISSOURCE|Indique que l’élément d'où proviennent les événements que le script peut recevoir. Objets enfants (les propriétés de l’objet qui sont eux-mêmes des objets) peuvent également extraire des événements au script. Ce n’est pas récursive, mais il fournit un mécanisme commode pour le cas courant, par exemple, de la création des contrôles d’un conteneur et tous ses membres.|  
|SCRIPTITEM_ISVISIBLE|Indique que le nom de l’élément est disponible dans l’espace de noms du script, autoriser l’accès aux propriétés, méthodes et événements de l’élément. Par convention, les propriétés de l’élément incluent enfants de l’élément ; Par conséquent, toutes les propriétés de l’objet enfant et les méthodes (et leurs enfants, de manière récursive) seront plus accessibles.|  
|SCRIPTITEM_NOCODE|Indique que l’élément est simplement un nom qui est ajouté à l’espace de noms du script et ne doit pas être considérée comme un élément pour lequel le code doit être associé. Par exemple, sans cet indicateur est défini, VBScript créera un module séparé pour l’élément nommé, et C++ peuvent créer une classe wrapper séparé pour l’élément nommé.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé).|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)