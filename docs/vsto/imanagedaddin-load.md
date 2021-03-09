---
title: IManagedAddIn::Load
description: Appelée quand un complément VSTO managé est chargé.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fc89ba13e9fc0f62b264cdb926e1a8392c0b41bd
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469760"
---
# <a name="imanagedaddinload"></a>IManagedAddIn::Load
  Appelée quand un complément VSTO managé est chargé.

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*bstrManifestURL*|Chemin d’accès complet du manifeste du complément VSTO.|
|*pdispApplication*|Pointeur vers un IDispatch qui représente l’application hôte qui charge le complément VSTO.|

## <a name="return-value"></a>Valeur renvoyée
 Valeur HRESULT qui indique si la méthode a réussi.

## <a name="remarks"></a>Notes
 Un manifeste est un fichier (en général, un fichier XML) qui fournit des informations qui sont utilisées pour charger le complément VSTO. Par exemple, un manifeste peut spécifier l’emplacement de l’assembly du complément VSTO et la classe de point d’entrée à instancier lors du chargement du complément VSTO.

 Le paramètre *bstrManifestURL* contient la valeur de l' `Manifest` entrée sous la clé de Registre **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \Addins \\ _\<add-in ID>_** pour le complément VSTO. Pour plus d’informations, consultez [IManagedAddin interface](../vsto/imanagedaddin-interface.md).

 Implémentez la méthode [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) pour effectuer des tâches telles que la configuration de la stratégie de sécurité et du domaine d’application pour le complément VSTO chargé.

## <a name="see-also"></a>Voir aussi
- [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
