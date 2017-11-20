---
title: IManagedAddin::Load | Documents Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 62c1af72158c0b416942e9124003dbeb06b584ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Appelée quand un complément VSTO managé est chargé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*bstrManifestURL*|Chemin d’accès complet du manifeste du complément VSTO.|  
|*pdispApplication*|Pointeur vers un IDispatch qui représente l’application hôte qui charge le composant logiciel complément VSTO.|  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur HRESULT qui indique si la méthode a réussi.  
  
## <a name="remarks"></a>Remarques  
 Un manifeste est un fichier (en général un fichier XML) qui fournit des informations utilisées pour aider à charger le complément VSTO. Par exemple, un manifeste peut spécifier l’emplacement de l’assembly du complément VSTO et la classe de point d’entrée à instancier lors du chargement du complément VSTO.  
  
 Le *bstrManifestURL* paramètre contient la valeur de la `Manifest` entrée sous le HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<nom de l’application >*\Addins\\*\<id_complément >* clé de Registre pour le composant logiciel complément VSTO. Pour plus d'informations, consultez [IManagedAddin Interface](../vsto/imanagedaddin-interface.md).  
  
 Implémentez la méthode [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) pour effectuer des tâches telles que la configuration de la stratégie de sécurité et du domaine d’application pour le complément VSTO chargé.  
  
## <a name="see-also"></a>Voir aussi  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  