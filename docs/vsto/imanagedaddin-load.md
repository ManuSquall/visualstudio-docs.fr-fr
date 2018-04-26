---
title: IManagedAddin::Load | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 545560c5f02437925c2f93e9c6dc3113e1cddd0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
## <a name="remarks"></a>Notes  
 Un manifeste est un fichier (en général un fichier XML) qui fournit des informations utilisées pour aider à charger le complément VSTO. Par exemple, un manifeste peut spécifier l’emplacement de l’assembly du complément VSTO et la classe de point d’entrée à instancier lors du chargement du complément VSTO.  
  
 Le *bstrManifestURL* paramètre contient la valeur de la `Manifest` entrée sous le HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<nom de l’application >* \Addins\\*\<id_complément >* clé de Registre pour le composant logiciel complément VSTO. Pour plus d'informations, consultez [IManagedAddin Interface](../vsto/imanagedaddin-interface.md).  
  
 Implémentez la méthode [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) pour effectuer des tâches telles que la configuration de la stratégie de sécurité et du domaine d’application pour le complément VSTO chargé.  
  
## <a name="see-also"></a>Voir aussi  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  