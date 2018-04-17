---
title: Prise en charge pour les paramètres utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cf2ba79cc8bff57de1fd410f8a2780825d693181
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="support-for-user-settings"></a>Prise en charge pour les paramètres utilisateur
Un VSPackage peut définir une ou plusieurs catégories de paramètres, qui sont des groupes de variables d’état qui demeurent lorsqu’un utilisateur choisit le **paramètres d’importation/exportation** commande sur le **outils** menu. Pour activer cette persistance, vous utilisez les paramètres API dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 Une entrée de Registre est désigné comme un Point de paramètres personnalisés et un GUID définit la catégorie de paramètres d’un VSPackage. Un VSPackage peut prendre en charge plusieurs catégories de paramètres, chacun définis par un Point de paramètres personnalisés.  
  
-   Les implémentations de paramètres qui sont basées sur les assemblys d’interopérabilité (à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interface) doit créer le Point de paramètres personnalisés en modifiant le Registre ou à l’aide d’un script de Registre (fichier .rgs). Pour plus d’informations, consultez [création de Scripts de bureau d’enregistrement](/cpp/atl/creating-registrar-scripts).  
  
-   Le code qui utilise Managed Package Framework (MPF) doit-elle créer des Points de paramètres personnalisés en associant un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> pour le VSPackage pour chaque Point de paramètres personnalisés.  
  
     Si un VSPackage unique prend en charge plusieurs Points de paramètres personnalisés, chaque Point de paramètres personnalisés est implémentée par une classe distincte, et chacun est enregistré par une instance unique de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe. Par conséquent, une classe d’implémentation de paramètres peuvent prendre en charge plusieurs catégories de paramètres.  
  
## <a name="custom-settings-point-registry-entry-details"></a>Détails de l’entrée des paramètres personnalisés du Registre de Point  
 Points de paramètres personnalisés sont créés dans une entrée de Registre à l’emplacement suivant : HKLM\Software\Microsoft\VisualStudio\\*\<Version >*\UserSettings\\`<CSPName>`, où `<CSPName>` est le nom du Point de paramètres personnalisés le prend en charge VSPackage et  *\<Version >* est la version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], par exemple 8.0.  
  
> [!NOTE]
>  Le chemin d’accès racine de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* peut être remplacée par une autre racine lorsque le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est de l’environnement de développement intégré (IDE) initialisé. Pour plus d’informations, consultez [les commutateurs de ligne de commande](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 La structure de l’entrée de Registre est illustrée ci-dessous :  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<Version >*\UserSettings\  
  
 `<CSPName`> = s '#12345'  
  
 Package = '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 Catégorie = '{AAAAAA aaaa jj aaaa YYYYYYYYY}'  
  
 ResourcePackage = '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 AlternateParent = nom de catégorie  
  
|Name|Type|Données|Description|  
|----------|----------|----------|-----------------|  
|(Default)|REG_SZ|Nom du Point de paramètres personnalisés|Nom de la clé, `<CSPName`>, est le nom non localisé du Point de paramètres personnalisés.<br /><br /> Pour les implémentations basées sur MPF, son nom est obtenu en combinant les `categoryName` et `objectName` arguments de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructeur dans `categoryName_objectName`.<br /><br /> La clé peut être vide ou il peut contenir l’ID de référence à la chaîne localisée dans une DLL satellite. Cette valeur est obtenue à partir de la `objectNameResourceID` l’argument de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructeur.|  
|Package|REG_SZ|GUID|Le GUID du VSPackage qui implémente le Point de paramètres personnalisés.<br /><br /> Implémentations basés sur MPF à l’aide de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> de classe, utilisez le constructeur `objectType` argument contenant le package Visual Studio <xref:System.Type> et de la réflexion pour obtenir cette valeur.|  
|Category|REG_SZ|GUID|GUID qui identifie la catégorie de paramètres.<br /><br /> Pour les implémentations basées sur les assemblys PIA, cette valeur peut être arbitrairement choisis GUID, qui le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE passe à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> méthodes. Toutes les implémentations de ces deux méthodes doivent vérifier leurs arguments GUID.<br /><br /> Pour les implémentations basées sur MPF, ce GUID est obtenu par la <xref:System.Type> de la classe implémentant le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mécanisme de paramètres.|  
|ResourcePackage|REG_SZ|GUID|Facultatif.<br /><br /> Chemin d’accès au satellite DLL contenant des chaînes localisées si l’implémentation VSPackage ne fournit pas les.<br /><br /> MPF utilise la réflexion pour obtenir la bonne ressource VSPackage, donc la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe ne définit pas cet argument.|  
|AlternateParent|REG_SZ|Nom du dossier dans la page Outils/Options contenant ce Point de paramètres personnalisés.|Facultatif.<br /><br /> Vous devez définir cette valeur uniquement si une implémentation de paramètres prend en charge **Outils Options** des pages qui utilisent le mécanisme de persistance dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] plutôt que le mécanisme dans le modèle automation pour enregistrer l’état.<br /><br /> Dans ces cas, la valeur de la clé AlternateParent est la `topic` section de la `topic.sub-topic` chaîne utilisée pour identifier le notamment **OutilsOptions** page. Par exemple, pour le **OutilsOptions** page `"TextEditor.Basic"` la valeur de AlternateParent serait `"TextEditor"`.<br /><br /> Lorsque <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> génère le Point de paramètres personnalisés, il est le même que le nom de catégorie.|