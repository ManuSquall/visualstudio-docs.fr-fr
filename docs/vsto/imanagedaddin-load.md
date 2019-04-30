---
title: IManagedAddin::Load
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 87fb34e90d36383f49b6369fb1dea4b9854c7300
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956729"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
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
|*pdispApplication*|Pointeur vers un IDispatch qui représente l’application hôte est en cours de chargement du complément, VSTO.|

## <a name="return-value"></a>Valeur de retour
 Valeur HRESULT qui indique si la méthode a réussi.

## <a name="remarks"></a>Notes
 Un manifeste est un fichier (en général un fichier XML) qui fournit des informations utilisées pour aider à charger le complément VSTO. Par exemple, un manifeste peut spécifier l’emplacement de l’assembly du complément VSTO et la classe de point d’entrée à instancier lors du chargement du complément VSTO.

 Le *bstrManifestURL* paramètre contient la valeur de la `Manifest` entrée sous le **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<nom de l’application >_ \Addins\\_\<id_complément >_**  clé de Registre pour le composant logiciel complément VSTO. Pour plus d’informations, consultez [interface IManagedAddin](../vsto/imanagedaddin-interface.md).

 Implémentez la méthode [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) pour effectuer des tâches telles que la configuration de la stratégie de sécurité et du domaine d’application pour le complément VSTO chargé.

## <a name="see-also"></a>Voir aussi
- [IManagedAddin, interface](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
