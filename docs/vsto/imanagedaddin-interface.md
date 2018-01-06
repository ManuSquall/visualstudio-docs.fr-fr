---
title: Interface IManagedAddin | Documents Microsoft
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
helpviewer_keywords: IManagedAddin interface
ms.assetid: 5350629c-6cf8-42dd-ae65-3f34322ee10f
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: be74604bfabde34f2046af98ac976abd37068022
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imanagedaddin-interface"></a>interface IManagedAddin
  Implémentez l’interface IManagedAddin pour créer un composant qui charge gérée des Compléments VSTO. Cette interface a été ajoutée dans la version 2007 de Microsoft Office System.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes qui sont définies par l’interface IManagedAddin.  
  
|Name|Description|  
|----------|-----------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Appelée quand une application Microsoft Office charge un complément VSTO géré.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Appelée juste avant qu’une application Microsoft Office décharge un complément VSTO géré.|  
  
## <a name="remarks"></a>Notes  
 Les applications Microsoft Office, en commençant par le système de Microsoft Office 2007, utilisent l’interface IManagedAddin pour charger les Compléments VSTO Office. Vous pouvez implémenter l’interface IManagedAddin pour créer vos propres chargeur de complément VSTO et de runtime pour gérés des Compléments VSTO, au lieu d’utiliser le chargeur de complément VSTO (VSTOLoader.dll) et [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Pour plus d'informations, consultez [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
## <a name="how-managed-add-ins-are-loaded"></a>Mode de chargement des compléments gérés  
 Les étapes suivantes se produisent au démarrage d’une application :  
  
1.  L’application découvre les compléments VSTO en recherchant des entrées sous la clé de Registre suivante :  
  
     HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<nom de l’application >*\Addins\  
  
     Chaque entrée sous cette clé de Registre est un ID unique du complément VSTO. En règle générale, il s’agit du nom de l’assembly du complément VSTO.  
  
2.  L’application cherche une entrée `Manifest` sous l’entrée de chaque complément VSTO.  
  
     Compléments VSTO gérés peuvent stocker le chemin d’accès complet d’un manifeste dans le `Manifest` entrée sous HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<nom de l’application >*\Addins\\  *\<id_complément >*. Un manifeste est un fichier (en général un fichier XML) qui fournit des informations utilisées pour aider à charger le complément VSTO.  
  
3.  Si l’application trouve une entrée `Manifest` , elle essaie de charger un composant de chargeur de complément VSTO géré. Pour cela, l’application essaie de créer un objet COM qui implémente l’interface IManagedAddin.  
  
     La [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] inclut un composant de chargeur du complément VSTO (VSTOLoader.dll), ou vous pouvez créer le vôtre en implémentant de l’interface IManagedAddin.  
  
4.  L’application appelle la méthode [IManagedAddin::Load](../vsto/imanagedaddin-load.md) et passe la valeur de l’entrée `Manifest` .  
  
5.  La méthode [IManagedAddin::Load](../vsto/imanagedaddin-load.md) effectue les tâches requises pour charger le complément VSTO, notamment la configuration du domaine d’application et de la stratégie de sécurité pour le complément VSTO chargé.  
  
 Pour plus d’informations sur le Registre clés permettant des applications Microsoft Office découvrent et chargent les gérés des Compléments VSTO, consultez [les entrées de Registre pour les Compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="guidance-for-implementing-imanagedaddin"></a>Instructions pour l’implémentation d’IManagedAddin  
 Si vous implémentez IManagedAddin, vous devez inscrire la DLL qui contient l’implémentation à l’aide du CLSID suivant :  
  
 99D651D7-5F7C-470E-8A3B-774D5D9536AC  
  
 Applications Microsoft Office utilisent ce CLSID pour créer l’objet COM qui implémente IManagedAddin.  
  
> [!CAUTION]  
>  Ce CLSID est également utilisé par VSTOLoader.dll dans [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Par conséquent, si vous utilisez IManagedAddin pour créer vos propres chargeur de complément VSTO et le composant d’exécution, vous ne pouvez déployer votre composant sur des ordinateurs qui exécutent des Compléments VSTO qui s’appuient sur la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des API non managées &#40; développement Office dans Visual Studio &#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  