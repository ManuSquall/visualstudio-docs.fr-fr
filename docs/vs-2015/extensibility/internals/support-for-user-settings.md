---
title: Prise en charge pour les paramètres utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 445f95b1c52b5ada41918cf0f7d8120d912c209f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759903"
---
# <a name="support-for-user-settings"></a>Prise en charge des paramètres utilisateur
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un VSPackage peut définir une ou plusieurs catégories de paramètres qui sont des groupes de variables d’état qui persistent lorsqu’un utilisateur choisit le **importer/exporter les paramètres** commande sur le **outils** menu. Pour activer cette persistance, vous utilisez les paramètres API dans le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
 Une entrée de Registre qui est appelée un Point de paramètres personnalisés et un GUID définit la catégorie de paramètres d’un VSPackage. Un VSPackage peut prendre en charge plusieurs catégories de paramètres, chacun défini par un Point de paramètres personnalisés.  
  
-   Les implémentations de paramètres qui sont basées sur les assemblys d’interopérabilité (à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interface) doit créer le Point de paramètres personnalisés en modifiant le Registre ou à l’aide d’un script de bureau d’enregistrement (fichier .rgs). Pour plus d'informations, consultez [Creating Registrar Scripts](http://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35).  
  
-   Code qui utilise Managed Package Framework (MPF) doit créer des Points de paramètres personnalisés en attachant un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> au VSPackage pour chaque Point de paramètres personnalisés.  
  
     Si un VSPackage unique prend en charge plusieurs Points de paramètres personnalisés, chaque Point de paramètres personnalisés est implémentée par une classe distincte, et chacun est enregistré par une instance unique de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe. Par conséquent, une implémentation de classe de paramètres peuvent prendre en charge plusieurs catégories de paramètres.  
  
## <a name="custom-settings-point-registry-entry-details"></a>Détails des entrées du Registre de Point de paramètres personnalisés  
 Points de paramètres personnalisés sont créés dans une entrée de Registre à l’emplacement suivant : HKLM\Software\Microsoft\VisualStudio\\*\<Version >* \UserSettings\\`<CSPName>`, où `<CSPName>` est le nom du Point de paramètres personnalisé le prend en charge VSPackage et  *\<Version >* est la version de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], par exemple 8.0.  
  
> [!NOTE]
>  Le chemin d’accès racine de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* peut être remplacée par une autre racine quand le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est l’environnement de développement intégré (IDE) initialisé. Pour plus d’informations, consultez [les commutateurs de ligne de commande](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 La structure de l’entrée de Registre est illustrée ci-dessous :  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<Version >* \UserSettings\  
  
 `<CSPName`> = s '#12345'  
  
 Package = '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 Catégorie = '{AAAAAA jj aaaa aaaa YYYYYYYYY}'  
  
 ResourcePackage = '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 AlternateParent = nom de catégorie  
  
|Name|Type|Données|Description|  
|----------|----------|----------|-----------------|  
|(Default)|REG_SZ|Nom du Point de paramètres personnalisés|Nom de la clé, `<CSPName`>, est le nom non localisé du Point de paramètres personnalisés.<br /><br /> Pour les implémentations basées sur MPF, nom de la clé est obtenu en combinant le `categoryName` et `objectName` arguments de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructeur dans `categoryName_objectName`.<br /><br /> La clé peut être vide ou il peut contenir l’ID de référence à la chaîne localisée dans une DLL satellite. Cette valeur est obtenue à partir de la `objectNameResourceID` l’argument de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructeur.|  
|Package|REG_SZ|GUID|Le GUID du VSPackage qui implémente le Point de paramètres personnalisés.<br /><br /> Implémentations basées sur l’utilisation de MPF le <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> de classe, utilisez le constructeur `objectType` argument contenant le VSPackage <xref:System.Type> et de la réflexion pour obtenir cette valeur.|  
|Category|REG_SZ|GUID|GUID identifiant la catégorie de paramètres.<br /><br /> Pour les implémentations basées sur les assemblys PIA, cette valeur peut être arbitrairement choisis GUID, qui le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE transmet à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> et le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> méthodes. Toutes les implémentations de ces deux méthodes doivent vérifier leurs arguments GUID.<br /><br /> Pour les implémentations basées sur MPF, ce GUID est obtenu par le <xref:System.Type> de la classe implémentant le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mécanisme de paramètres.|  
|ResourcePackage|REG_SZ|GUID|Facultatif.<br /><br /> Chemin d’accès au satellite DLL contenant des chaînes localisées si le VSPackage implémentation ne fournit pas les.<br /><br /> MPF utilise la réflexion pour obtenir la ressource correcte VSPackage, donc la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe ne définit pas cet argument.|  
|AlternateParent|REG_SZ|Nom du dossier sous la page Outils/Options contenant ce Point de paramètres personnalisés.|Facultatif.<br /><br /> Vous devez définir cette valeur uniquement si une implémentation de paramètres prend en charge **Outils/Options** pages qui utilisent le mécanisme de persistance dans le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] plutôt que le mécanisme dans le modèle automation pour enregistrer l’état.<br /><br /> Dans ce cas, la valeur dans la clé AlternateParent est la `topic` section de la `topic.sub-topic` chaîne utilisée pour identifier le particulier **ToolsOptions** page. Par exemple, pour le **ToolsOptions** page `"TextEditor.Basic"` la valeur de AlternateParent serait `"TextEditor"`.<br /><br /> Lorsque <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> génère le Point de paramètres personnalisés, il est le même que le nom de catégorie.|

