---
title: interface IManagedAddin
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ddede8542cda7499a9781c19a6baf1c58acfd125
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839542"
---
# <a name="imanagedaddin-interface"></a>interface IManagedAddin
  Implémentez l’interface IManagedAddin pour créer un composant qui charge gérée des Compléments VSTO. Cette interface a été ajoutée dans la version 2007 de Microsoft Office System.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
 Les applications Microsoft Office, en commençant par le système Microsoft Office 2007, utilisent l’interface IManagedAddin pour charger les compléments Office VSTO. Vous pouvez implémenter l’interface IManagedAddin pour créer vos propres chargeur de complément VSTO et de runtime pour gérés des Compléments VSTO, au lieu d’utiliser le chargeur de complément VSTO (*VSTOLoader.dll*) et [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Pour plus d'informations, consultez [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
## <a name="how-managed-add-ins-are-loaded"></a>Comment les compléments managés sont chargés.  
 Les étapes suivantes se produisent au démarrage d’une application :  
  
1. L’application découvre les compléments VSTO en recherchant des entrées sous la clé de Registre suivante :  
  
    **HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<nom_application >* \Addins\\**  
  
    Chaque entrée sous cette clé de Registre est un ID unique du complément VSTO. En règle générale, il s’agit du nom de l’assembly du complément VSTO.  
  
2. L’application cherche une entrée `Manifest` sous l’entrée de chaque complément VSTO.  
  
    Compléments VSTO managés peuvent stocker le chemin d’accès complet d’un manifeste dans le `Manifest` entrée sous **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<nom_application >_ \Addins\\  _\<id_complément >_**. Un manifeste est un fichier (en général un fichier XML) qui fournit des informations utilisées pour aider à charger le complément VSTO.  
  
3. Si l’application trouve une entrée `Manifest` , elle essaie de charger un composant de chargeur de complément VSTO géré. Pour cela, l’application essaie de créer un objet COM qui implémente l’interface IManagedAddin.  
  
    Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] inclut un composant de chargeur de complément VSTO (*VSTOLoader.dll*), ou vous pouvez créer le vôtre en implémentant l’interface IManagedAddin.  
  
4. L’application appelle la méthode [IManagedAddin::Load](../vsto/imanagedaddin-load.md) et passe la valeur de l’entrée `Manifest` .  
  
5. La méthode [IManagedAddin::Load](../vsto/imanagedaddin-load.md) effectue les tâches requises pour charger le complément VSTO, notamment la configuration du domaine d’application et de la stratégie de sécurité pour le complément VSTO chargé.  
  
   Pour plus d’informations sur le Registre clés qui utilisent des applications Microsoft Office pour découvrir et charger gérés des Compléments VSTO, consultez [les entrées de Registre pour les Compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="guidance-to-implement-imanagedaddin"></a>Conseils pour implémenter IManagedAddin  
 Si vous implémentez IManagedAddin, vous devez inscrire la DLL qui contient l’implémentation à l’aide du CLSID suivant :  
  
 99D651D7-5F7C-470E-8A3B-774D5D9536AC  
  
 Applications Microsoft Office utilisent ce CLSID pour créer l’objet COM qui implémente IManagedAddin.  
  
> [!CAUTION]  
>  Ce CLSID est également utilisé par *VSTOLoader.dll* dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Par conséquent, si vous utilisez IManagedAddin pour créer vos propres chargeur de complément VSTO et le composant d’exécution, vous ne pouvez pas déployer votre composant sur des ordinateurs qui exécutent des Compléments VSTO qui s’appuient sur le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des API non managées &#40;développement Office dans Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  