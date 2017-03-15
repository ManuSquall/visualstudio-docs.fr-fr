---
title: "Prise en charge pour les param&#232;tres utilisateur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Points de paramètres personnalisés"
  - "prise en charge des paramètres utilisateur (Visual Studio SDK), l’enregistrement de persistance"
  - "persistance, l’enregistrement des paramètres"
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Prise en charge pour les param&#232;tres utilisateur
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage peut définir une ou plusieurs catégories de paramètres, qui sont des groupes de variables d’état persistant lorsqu’un utilisateur choisit le **importation et exportation de paramètres** sur la **outils** menu. Pour activer cette persistance, vous utilisez les paramètres API dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 Une entrée de Registre qui correspond à un Point de paramètres personnalisé et un GUID définit la catégorie de paramètres d’un VSPackage. Un VSPackage peut prendre en charge plusieurs catégories de paramètres, chacun défini par un Point de paramètres personnalisés.  
  
-   Les implémentations de paramètres qui sont basées sur les assemblys d’interopérabilité \(à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interface\) doit créer Point de paramètres personnalisé en modifiant le Registre ou à l’aide d’un script d’inscription \(fichier .rgs\). Pour plus d'informations, consultez [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts).  
  
-   Le code qui utilise Managed Package Framework \(MPF\) doit créer des Points de paramètres personnalisés en associant un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> pour le VSPackage pour chaque Point de paramètres personnalisés.  
  
     Si un VSPackage unique prend en charge plusieurs Points de paramètres personnalisés, chaque Point de paramètres personnalisé est implémenté par une classe distincte, et chacun est enregistré par une instance unique de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe. Par conséquent, un paramètre de l’implémentation de classe peut prendre en charge plusieurs paramètres de catégorie.  
  
## Détails des entrées de Registre du Point des paramètres personnalisés  
 Points de paramètres personnalisés sont créés dans une entrée de Registre à l’emplacement suivant : HKLM\\Software\\Microsoft\\VisualStudio\\*\< Version \>*\\UserSettings\\`<CSPName>`, où `<CSPName>` est le nom du Point de paramètres personnalisés le prend en charge VSPackage et *\< Version \>* est la version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], par exemple 8.0.  
  
> [!NOTE]
>  Le chemin d’accès racine de HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< Version \>* peut être remplacée par une autre racine lorsque les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré \(IDE\) est initialisé. Pour plus d'informations, consultez [Commutateurs de ligne de commande](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 La structure de l’entrée de Registre est illustrée ci\-dessous :  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\< Version \>*\\UserSettings\\  
  
 `<CSPName`\> \= s '\#12345'  
  
 Package \= '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 Catégorie \= '{AAAAAA jj aaaa aaaa YYYYYYYYY}'  
  
 ResourcePackage \= '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 AlternateParent \= nom de la catégorie  
  
|Nom|Type|Données|Description|  
|---------|----------|-------------|-----------------|  
|\(Default\)|REG\_SZ|Nom du Point de paramètres personnalisés|Nom de la clé, `<CSPName`\>, est le nom non localisé du Point de paramètres personnalisés.<br /><br /> Pour les implémentations basées sur MPF, son nom est obtenu en combinant les `categoryName` et `objectName` arguments de le <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructeur dans `categoryName_objectName`.<br /><br /> La clé peut être vide ou il peut contenir l’ID de référence à la chaîne localisée dans une DLL satellite. Cette valeur est obtenue à partir de la `objectNameResourceID` l’argument de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructeur.|  
|Package|REG\_SZ|GUID|GUID du package VS qui implémente le Point de paramètres personnalisés.<br /><br /> Implémentations basées sur l’utilisation de MPF le <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> de classe, utilisez le constructeur `objectType` argument contenant le VSPackage <xref:System.Type> et de la réflexion pour obtenir cette valeur.|  
|Catégorie|REG\_SZ|GUID|GUID qui identifie la catégorie de paramètres.<br /><br /> Pour les implémentations basées sur les assemblys PIA, cette valeur peut être arbitrairement choisis GUID, qui le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE transmet à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> et le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> méthodes. Toutes les implémentations de ces deux méthodes doivent vérifier leurs arguments GUID.<br /><br /> Pour les implémentations basées sur MPF, ce GUID est obtenu par le <xref:System.Type> de la classe implémentant le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le mécanisme de paramètres.|  
|ResourcePackage|REG\_SZ|GUID|Facultatif.<br /><br /> Chemin d’accès au satellite DLL contenant des chaînes localisées si le VSPackage implémentation ne fournit pas les.<br /><br /> MPF utilise la réflexion pour obtenir les ressources correctes VSPackage, donc la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe ne définit pas cet argument.|  
|AlternateParent|REG\_SZ|Nom du dossier dans la page Outils\/Options contenant ce Point de paramètres personnalisés.|Facultatif.<br /><br /> Vous devez définir cette valeur uniquement si une implémentation de paramètres prend en charge **Outils\/Options** les pages qui utilisent le mécanisme de persistance dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] plutôt que le mécanisme dans le modèle automation pour enregistrer l’état.<br /><br /> Dans ce cas, la valeur de la clé AlternateParent est la `topic` section de la `topic.sub-topic` chaîne utilisée pour identifier le particulier **outilsOptions** page. Par exemple, pour le **outilsOptions** page `"TextEditor.Basic"` la valeur de AlternateParent est `"TextEditor"`.<br /><br /> Lorsque <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> génère le Point de paramètres personnalisés, il est le même que le nom de catégorie.|