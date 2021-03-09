---
title: interface IManagedAddin
description: Implémentez l’interface IManagedAddin pour créer un composant qui charge les compléments VSTO managés.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 614cf7e8d0e682d894328fb764c6d64b855d2834
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469786"
---
# <a name="imanagedaddin-interface"></a>interface IManagedAddin
  Implémentez l’interface IManagedAddin pour créer un composant qui charge les compléments VSTO managés. Cette interface a été ajoutée au système 2007 Microsoft Office.

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
 Le tableau suivant répertorie les méthodes définies par l’interface IManagedAddin.

|Nom|Description|
|----------|-----------------|
|[IManagedAddIn::Load](../vsto/imanagedaddin-load.md)|Appelée quand une application Microsoft Office charge un complément VSTO géré.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Appelée juste avant qu’une application Microsoft Office décharge un complément VSTO géré.|

## <a name="remarks"></a>Notes
 Microsoft Office les applications, en commençant par le système 2007 Microsoft Office, utilisez l’interface IManagedAddin pour faciliter le chargement des compléments VSTO Office. Vous pouvez implémenter l’interface IManagedAddin pour créer votre propre chargeur et Runtime de complément VSTO pour les compléments VSTO managés, au lieu d’utiliser le chargeur de complément VSTO (*VSTOLoader.dll*) et [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Pour plus d'informations, consultez [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

## <a name="how-managed-add-ins-are-loaded"></a>Mode de chargement des compléments gérés
 Les étapes suivantes se produisent au démarrage d’une application :

1. L’application découvre les compléments VSTO en recherchant des entrées sous la clé de Registre suivante :

    **HKEY_CURRENT_USER\Software\Microsoft\Office\\ *\<application name>* \Addins\\**

    Chaque entrée sous cette clé de Registre est un ID unique du complément VSTO. En règle générale, il s’agit du nom de l’assembly du complément VSTO.

2. L’application cherche une entrée `Manifest` sous l’entrée de chaque complément VSTO.

    Les compléments VSTO managés peuvent stocker le chemin d’accès complet d’un manifeste dans l' `Manifest` entrée sous **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \Addins \\ _\<add-in ID>_**. Un manifeste est un fichier (en général, un fichier XML) qui fournit des informations qui sont utilisées pour charger le complément VSTO.

3. Si l’application trouve une entrée `Manifest` , elle essaie de charger un composant de chargeur de complément VSTO géré. Pour ce faire, l’application essaie de créer un objet COM qui implémente l’interface IManagedAddin.

    Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] comprend un composant de chargeur de complément VSTO (*VSTOLoader.dll*), ou vous pouvez créer votre propre composant en implémentant l’interface IManagedAddin.

4. L’application appelle la méthode [IManagedAddin::Load](../vsto/imanagedaddin-load.md) et passe la valeur de l’entrée `Manifest` .

5. La méthode [IManagedAddin::Load](../vsto/imanagedaddin-load.md) effectue les tâches requises pour charger le complément VSTO, notamment la configuration du domaine d’application et de la stratégie de sécurité pour le complément VSTO chargé.

   Pour plus d’informations sur les clés de registre que Microsoft Office applications utilise pour découvrir et charger des compléments VSTO gérés, consultez [entrées du Registre pour les compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="guidance-to-implement-imanagedaddin"></a>Guide d’implémentation de IManagedAddin
 Si vous implémentez IManagedAddin, vous devez inscrire la DLL qui contient l’implémentation à l’aide du CLSID suivant :

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Les applications Microsoft Office utilisent ce CLSID pour créer l’objet COM qui implémente IManagedAddin.

> [!CAUTION]
> Ce CLSID est également utilisé par les *VSTOLoader.dll* dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Par conséquent, si vous utilisez IManagedAddin pour créer votre propre composant d’exécution et le chargeur de complément VSTO, vous ne pouvez pas déployer votre composant sur les ordinateurs qui exécutent des compléments VSTO qui reposent sur le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur les API non managées &#40;le développement Office dans Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
