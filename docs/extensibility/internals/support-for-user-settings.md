---
title: Prise en charge des paramètres utilisateur | Microsoft Docs
description: Découvrez comment activer la persistance des catégories de paramètres à l’aide des API de paramètres dans le kit de développement logiciel (SDK) Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e0128ce1f27674010d1b624457815ddb1016e016
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080643"
---
# <a name="support-for-user-settings"></a>Prise en charge des paramètres utilisateur
Un VSPackage peut définir une ou plusieurs catégories de paramètres, qui sont des groupes de variables d’État qui persistent lorsqu’un utilisateur choisit la commande **Importer/exporter les paramètres** dans le menu **Outils** . Pour activer cette persistance, vous utilisez les API de paramètres dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 Une entrée de Registre appelée point de paramètres personnalisés et un GUID définit la catégorie de paramètres d’un VSPackage. Un VSPackage peut prendre en charge plusieurs catégories de paramètres, chacune définie par un point de paramètres personnalisés.

- Les implémentations de paramètres basés sur des assemblys d’interopérabilité (à l’aide de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interface) doivent créer un point de paramètres personnalisés en modifiant le registre ou à l’aide d’un script d’inscription (fichier. RGS). Pour plus d'informations, consultez [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- Le code qui utilise Managed package Framework (MPF) doit créer des points de paramètres personnalisés en joignant un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> au VSPackage pour chaque point de paramètres personnalisés.

     Si un VSPackage unique prend en charge plusieurs points de paramètres personnalisés, chaque point de paramètres personnalisés est implémenté par une classe distincte, et chacun est inscrit par une instance unique de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe. Par conséquent, les paramètres de la classe qui implémentent peuvent prendre en charge plusieurs catégories de paramètres.

## <a name="custom-settings-point-registry-entry-details"></a>Détails de l’entrée de Registre du point de paramètres personnalisés
 Les points de paramètres personnalisés sont créés dans une entrée de Registre à l’emplacement suivant : HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \UserSettings \\ `<CSPName>` , où `<CSPName>` est le nom du point de paramètres personnalisés pris en charge par le VSPackage et *\<Version>* est la version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , par exemple 8,0.

> [!NOTE]
> Le chemin d’accès racine de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<Version>* peut être substitué par une autre racine lorsque l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE) est initialisé. Pour plus d’informations, consultez [commutateurs de ligne de commande](../../extensibility/command-line-switches-visual-studio-sdk.md).

 La structure de l’entrée de Registre est illustrée ci-dessous :

 HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \UserSettings\

 `<CSPName`>= s' #12345 '

 Package = ' {XXXXXX XXXX XXXX XXXX XXXXXXXXs} '

 Category = ' {YYYYYY YYYY yyyy yyyy YYYYYYYYY} '

 ResourcePackage = ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ} '

 AlternateParent = CategoryName

| Nom | Type | Données | Description |
|-----------------|--------| - | - |
| (Par défaut) | REG_SZ | Nom du point de paramètres personnalisés | Le nom de la clé, `<CSPName`>, est le nom non localisé du point de paramètres personnalisés.<br /><br /> Pour les implémentations basées sur MPF, le nom de la clé est obtenu en combinant les `categoryName` `objectName` arguments et du <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructeur dans `categoryName_objectName` .<br /><br /> La clé peut être vide ou contenir l’ID de référence à la chaîne localisée dans une DLL satellite. Cette valeur est obtenue à partir de l' `objectNameResourceID` argument du <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructeur. |
| Package | REG_SZ | GUID | GUID du VSPackage qui implémente le point de paramètres personnalisés.<br /><br /> Implémentations basées sur MPF à l’aide de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe, utilisez l’argument du constructeur `objectType` contenant les VSPackage <xref:System.Type> et la réflexion pour obtenir cette valeur. |
| Category | REG_SZ | GUID | GUID identifiant la catégorie de paramètres.<br /><br /> Pour les implémentations basées sur des assemblys d’interopérabilité, cette valeur peut être un GUID choisi arbitrairement, que l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE passe aux <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> méthodes et. Toutes les implémentations de ces deux méthodes doivent vérifier leurs arguments GUID.<br /><br /> Pour les implémentations basées sur MPF, ce GUID est obtenu par le <xref:System.Type> de la classe qui implémente le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mécanisme de paramètres. |
| ResourcePackage | REG_SZ | GUID | Optionnel.<br /><br /> Chemin d’accès à la DLL satellite contenant des chaînes localisées si le VSPackage d’implémentation ne les fournit pas.<br /><br /> MPF utilise la réflexion pour obtenir le VSPackage de ressources correct, donc la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe ne définit pas cet argument. |
| AlternateParent | REG_SZ | Nom du dossier sous la page Outils Options contenant ce point de paramètres personnalisés. | Optionnel.<br /><br /> Vous devez définir cette valeur uniquement si une implémentation de paramètres prend en charge les pages d' **Options des outils** qui utilisent le mécanisme de persistance dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] plutôt que le mécanisme dans le modèle Automation pour enregistrer l’État.<br /><br /> Dans ce cas, la valeur de la clé AlternateParent est la `topic` section de la `topic.sub-topic` chaîne utilisée pour identifier la page **OutilsOptions** particulière. Par exemple, pour la page **OutilsOptions** , `"TextEditor.Basic"` la valeur de AlternateParent serait `"TextEditor"` .<br /><br /> Lorsque <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> génère le point de paramètres personnalisés, il est identique au nom de la catégorie. |
