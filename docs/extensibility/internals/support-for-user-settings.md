---
title: Prise en charge des paramètres de l’utilisateur ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02bb2450196de76917e9cffc2f5f5acc6c8ee7b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704791"
---
# <a name="support-for-user-settings"></a>Prise en charge des paramètres utilisateur
Un VSPackage peut définir une ou plusieurs catégories de paramètres, qui sont des groupes de variables d’état qui persistent lorsqu’un utilisateur choisit la commande **Paramètres d’importation/exportation** sur le menu **Outils.** Pour activer cette persistance, vous utilisez [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]les paramètres API dans le .

 Une inscription au registre appelée point de paramètres personnalisés et un GUID définit la catégorie des paramètres d’un VSPackage. Un VSPackage peut prendre en charge plusieurs catégories de paramètres, chacune définie par un point de paramètres personnalisé.

- Les implémentations de paramètres basés sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> des assemblages interop (à l’aide de l’interface) devraient créer le point de paramètres personnalisés en modifiant le registre ou en utilisant un script registraire (.rgs fichier). Pour plus d'informations, consultez [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- Le code qui utilise le cadre de paquet géré (MPF) devrait créer des points de paramètres personnalisés en attachant un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> à l’emballage VS pour chaque point de paramètres personnalisé.

     Si un seul VSPackage prend en charge plusieurs points de paramètres personnalisés, chaque point de <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> paramètres personnalisés est implémenté par une classe distincte, et chacun est enregistré par une instance unique de la classe. Par conséquent, une classe de mise en œuvre de paramètres peut prendre en charge plus d’une catégorie de paramètres.

## <a name="custom-settings-point-registry-entry-details"></a>Détails d’entrée du registre des paramètres personnalisés
 Paramètres personnalisés Les points sont créés dans une entrée de registre à l’emplacement suivant : HKLM-Software-Microsoft-VisualStudio\\*\<Version>*'UserSettings , où\\`<CSPName>` `<CSPName>` se trouve le nom du point de paramètres personnalisés que le vsPackage prend en charge et * \<la version>* est la version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], par exemple 8.0.

> [!NOTE]
> Le chemin radiculaire de HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio\\*\<Version>* peut être remplacé par une [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] racine alternative lorsque l’environnement de développement intégré (IDE) est paralé. Pour plus d’informations, voir [Switches De ligne de commande](../../extensibility/command-line-switches-visual-studio-sdk.md).

 La structure de l’entrée du registre est illustrée ci-dessous :

 Version HKLM-Software-Microsoft-VisualStudio\\*\<>*'UserSettings'

 `<CSPName`>' '#12345'

 Forfait 'XXXXXX XXXX XXXX XXXX XXXXX XXXXXXXXXXXXXX'

 Catégorie 'YyyyyyYY YyyY YyyY YyyY Yyyy Yyyy yyyyyyyyyyYYYYY'

 ResourcePackage - 'ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZZZZZ'

 AlternateParent - CatégorieName

| Nom | Type | Données | Description |
|-----------------|--------| - | - |
| (Par défaut) | REG_SZ | Nom du point de paramètres personnalisés | Le nom de `<CSPName` la clé,>, est le nom non localisé du Point paramètres personnalisés.<br /><br /> Pour les implémentations basées sur le MPF, `categoryName` `objectName` le nom <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> de `categoryName_objectName`la clé est obtenu en combinant les arguments et les arguments du constructeur en .<br /><br /> La clé peut être vide, ou elle peut contenir l’ID de référence à la chaîne localisée dans un satellite DLL. Cette valeur est obtenue `objectNameResourceID` à <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> partir de l’argument au constructeur. |
| Package | REG_SZ | GUID | Le GUID du VSPackage qui implémente le point de paramètres personnalisés.<br /><br /> Implémentations basées <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> sur MPF à l’aide de la classe, utilisez l’argument du `objectType` constructeur contenant le VSPackage <xref:System.Type> et la réflexion pour obtenir cette valeur. |
| Category | REG_SZ | GUID | GUID identifiant la catégorie des paramètres.<br /><br /> Pour les implémentations basées sur les assemblages interop, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cette valeur peut <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> être <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> un GUID arbitrairement choisi, que l’IDE transmet aux méthodes et aux méthodes. Toutes les implémentations de ces deux méthodes doivent vérifier leurs arguments GUID.<br /><br /> Pour les implémentations basées sur le <xref:System.Type> MPF, ce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] GUID est obtenu par la classe mettant en œuvre le mécanisme de paramètres. |
| Emballage des ressources | REG_SZ | GUID | facultatif.<br /><br /> Chemin vers le satellite DLL contenant des chaînes localisées si la mise en œuvre VSPackage ne les fournit pas.<br /><br /> MPF utilise la réflexion pour obtenir la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> ressource correcte VSPackage, de sorte que la classe ne fixe pas cet argument. |
| AlternateParent (en) | REG_SZ | Nom du dossier sous la page Options Outils contenant ce point de paramètres personnalisé. | facultatif.<br /><br /> Vous ne devez définir cette valeur que si une implémentation de paramètres prend en charge les pages **Tools Options** qui utilisent le mécanisme de persistance dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] mécanisme plutôt que le mécanisme du modèle d’automatisation pour sauver l’état.<br /><br /> Dans ces cas, la valeur de la `topic` clé `topic.sub-topic` AlternateParent est la section de la chaîne utilisée pour identifier la page **ToolsOptions** particulière. Par exemple, pour la page `"TextEditor.Basic"` **ToolsOptions,** la `"TextEditor"`valeur de AlternateParent serait .<br /><br /> Lorsque <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> vous génèrez le point de paramètres personnalisé, il est le même que le nom de la catégorie. |
