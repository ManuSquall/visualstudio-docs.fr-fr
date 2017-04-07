---
title: "Prise en charge pour les paramètres utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 24bd28ad78f1cd3a21167215ed8348dc79edce6b
ms.lasthandoff: 04/05/2017

---
# <a name="support-for-user-settings"></a>Prise en charge pour les paramètres utilisateur
Un VSPackage peut définir une ou plusieurs catégories de paramètres, qui sont des groupes de variables d’état qui demeurent lorsqu’un utilisateur choisit le **paramètres d’importation/exportation** commande sur le **outils** menu. Pour activer cette persistance, vous utilisez les paramètres API dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 Une entrée de Registre est désigné comme un Point de paramètres personnalisés et un GUID définit la catégorie de paramètres d’un VSPackage. Un VSPackage peut prendre en charge plusieurs catégories de paramètres, chacun définis par un Point de paramètres personnalisés.  
  
-   Les implémentations de paramètres qui sont basées sur les assemblys d’interopérabilité (à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>interface) doit créer le Point de paramètres personnalisés en modifiant le Registre ou à l’aide d’un script de Registre (fichier .rgs).</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> Pour plus d’informations, consultez [création de Scripts de bureau d’enregistrement](/cpp/atl/creating-registrar-scripts).  
  
-   Le code qui utilise Managed Package Framework (MPF) doit-elle créer des Points de paramètres personnalisés en associant un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>pour le VSPackage pour chaque Point de paramètres personnalisés.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
     Si un VSPackage unique prend en charge plusieurs Points de paramètres personnalisés, chaque Point de paramètres personnalisés est implémentée par une classe distincte, et chacun est enregistré par une instance unique de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>classe.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Par conséquent, une classe d’implémentation de paramètres peuvent prendre en charge plusieurs catégories de paramètres.  
  
## <a name="custom-settings-point-registry-entry-details"></a>Détails de l’entrée des paramètres personnalisés du Registre de Point  
 Points de paramètres personnalisés sont créés dans une entrée de Registre à l’emplacement suivant : HKLM\Software\Microsoft\VisualStudio\\*\<Version >*\UserSettings\\`<CSPName>`, où `<CSPName>` est le nom du Point de paramètres personnalisés le prend en charge VSPackage et *\<Version >* est la version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], par exemple 8.0.  
  
> [!NOTE]
>  Le chemin d’accès racine de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* peut être remplacée par une autre racine quand le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) est initialisé. Pour plus d’informations, consultez [les commutateurs de ligne de commande](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 La structure de l’entrée de Registre est illustrée ci-dessous :  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<Version >*\UserSettings\  
  
 `<CSPName`> = s '#12345'  
  
 Package = '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 Catégorie = '{AAAAAA aaaa jj aaaa YYYYYYYYY}'  
  
 ResourcePackage = '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 AlternateParent = nom de catégorie  
  
|Nom|Type|Données|Description|  
|----------|----------|----------|-----------------|  
|(Default)|REG_SZ|Nom du Point de paramètres personnalisés|Nom de la clé, `<CSPName`>, est le nom non localisé du Point de paramètres personnalisés.<br /><br /> Pour les implémentations basées sur MPF, son nom est obtenu en combinant les `categoryName` et `objectName` arguments de le <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>constructeur dans `categoryName_objectName`.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute><br /><br /> La clé peut être vide ou il peut contenir l’ID de référence à la chaîne localisée dans une DLL satellite. Cette valeur est obtenue à partir de la `objectNameResourceID` l’argument de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>constructeur.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|Package|REG_SZ|GUID|Le GUID du VSPackage qui implémente le Point de paramètres personnalisés.<br /><br /> Implémentations en fonction de l’aide de MPF le <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>de classe, utilisez le constructeur `objectType` argument contenant le package Visual Studio <xref:System.Type>et de la réflexion pour obtenir cette valeur.</xref:System.Type> </xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|Catégorie|REG_SZ|GUID|GUID qui identifie la catégorie de paramètres.<br /><br /> Pour les implémentations basées sur les assemblys PIA, cette valeur peut être arbitrairement choisis GUID, qui le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE passe à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>et le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>méthodes.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> Toutes les implémentations de ces deux méthodes doivent vérifier leurs arguments GUID.<br /><br /> Pour les implémentations basées sur MPF, ce GUID est obtenu par le <xref:System.Type>de la classe implémentant le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mécanisme de paramètres.</xref:System.Type>|  
|ResourcePackage|REG_SZ|GUID|Facultatif.<br /><br /> Chemin d’accès au satellite DLL contenant des chaînes localisées si l’implémentation VSPackage ne fournit pas les.<br /><br /> MPF utilise la réflexion pour obtenir la bonne ressource VSPackage, donc la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>classe ne définit pas cet argument.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|AlternateParent|REG_SZ|Nom du dossier dans la page Outils/Options contenant ce Point de paramètres personnalisés.|Facultatif.<br /><br /> Vous devez définir cette valeur uniquement si une implémentation de paramètres prend en charge **Outils Options** des pages qui utilisent le mécanisme de persistance dans le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] plutôt que le mécanisme dans le modèle automation pour enregistrer l’état.<br /><br /> Dans ces cas, est la valeur de la clé AlternateParent le `topic` section de la `topic.sub-topic` chaîne utilisée pour identifier le notamment **OutilsOptions** page. Par exemple, pour le **OutilsOptions** page `"TextEditor.Basic"` la valeur de AlternateParent serait `"TextEditor"`.<br /><br /> Lorsque <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>génère le Point de paramètres personnalisés, il est le même que le nom de catégorie.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|
