---
title: Prise en charge des catégories de paramètres | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- settings, supporting with Visual Studio SDK
- Visual Studio SDK, supporting settings
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
manager: jillfra
ms.openlocfilehash: b37fe476c7654cc21a3b81f4a68aa4abc0348bb1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948642"
---
# <a name="support-for-settings-categories"></a>Prise en charge des catégories de paramètres
Une catégorie de paramètres se compose d’un groupe d’options qui personnalisent l’environnement de développement intégré (IDE). Par exemple, des paramètres peuvent contrôler la disposition des fenêtres [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et le contenu des menus. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Dans le menu **Outils** , cliquez sur **Importation et exportation de paramètres** pour démarrer l’ **Assistant Importation et exportation de paramètres**. L’Assistant propose trois options : exporter, importer ou réinitialiser vos paramètres. Par exemple, si vous sélectionnez l’exportation, la page **Choisir les paramètres à exporter** de l’Assistant s’affiche.  
  
 Le contrôle d’arborescence dans le volet de navigation de cette page répertorie les catégories. Une catégorie est un groupe de paramètres associés qui apparaissent sous la forme d’un « point de paramètres personnalisés », autrement dit sous forme de case à cocher. Vous utilisez ces cases à cocher pour sélectionner les catégories à rendre persistantes dans un fichier .vsettings. L’Assistant vous permet de nommer le fichier .vsettings et de spécifier son chemin.  
  
> [!NOTE]
>  Les paramètres sont enregistrés ou restaurés en tant que catégorie, et les différents noms des paramètres ne sont pas affichés dans l’Assistant.  
  
 L’infrastructure MPF (Managed Package Framework) prend en charge la création de catégories de paramètres avec un minimum de code supplémentaire.  
  
-   Vous créez un VSPackage pour fournir un conteneur pour la catégorie en sous-classant la classe <xref:Microsoft.VisualStudio.Shell.Package>.  
  
-   Vous créez la catégorie proprement dite en la dérivant de la classe <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
-   Vous connectez les deux avec <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="support-for-settings-categories"></a>Prise en charge des catégories de paramètres  
 La classe <xref:Microsoft.VisualStudio.Shell.Package> prend en charge la création de catégories. La classe <xref:Microsoft.VisualStudio.Shell.DialogPage> implémente une catégorie. L’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage> propose ses propriétés publiques à un utilisateur en tant que catégorie. Pour plus d'informations, consultez [Creating a Settings Category](../extensibility/creating-a-settings-category.md).  
  
 La classe <xref:Microsoft.VisualStudio.Shell.DialogPage> implémente <xref:Microsoft.VisualStudio.Shell.IProfileManager>, qui fournit la persistance des pages d’options et des paramètres utilisateur. Les méthodes <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> et <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> conservent les paramètres dans un fichier .vssettings fourni par [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en tant que <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>, respectivement. La méthode <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A> réinitialise les paramètres à leurs valeurs par défaut.  
  
 La classe <xref:Microsoft.VisualStudio.Shell.DialogPage> fournit une implémentation de la méthode <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A> qui lit les paires nom-valeur dans le flux xml, et utilise la réflexion pour découvrir les propriétés publiques dans la classe dérivée <xref:Microsoft.VisualStudio.Shell.DialogPage>. Les propriétés dont les noms correspondent aux paires nom-valeur sont affectées des valeurs correspondantes.  
  
 L’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> utilise la réflexion pour découvrir les propriétés publiques dans la classe dérivée <xref:Microsoft.VisualStudio.Shell.DialogPage>, et écrit les noms et les valeurs des propriétés dans le flux XML en tant que paires nom-valeur.  
  
### <a name="settings-category-registry-path"></a>Chemin du Registre de catégorie de paramètres  
 Le chemin de Registre de la catégorie de paramètres est déterminé en combinant <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, le mot, UserSettings, la catégorie de paramètres et le nom du point de paramètres personnalisés. Les noms de la catégorie de paramètres et du point de paramètres personnalisés sont joints et séparés par un trait de soulignement pour former le nom canonique et non localisé qui apparaît dans le Registre. Par exemple, si la catégorie de paramètres est « Ma Catégorie », le nom du point de paramètres personnalisés « Mes paramètres » et l’ApplicationRegistryRoot HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, la catégorie de paramètres a la clé de Registre HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\UserSettings\Ma Catégorie_Mes paramètres.  
  
> [!NOTE]
>  Le nom canonique n’apparaît pas dans une interface utilisateur. Il est utilisé pour associer un nom lisible à la catégorie de paramètres, un peu comme un identificateur programmatique (ProgID).  
  
### <a name="settings-category-attribute"></a>Attribut de catégorie de paramètres  
 Le <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> détermine le mappage des catégories aux points de paramètres personnalisés dans le **Assistant Importation et exportation paramètres** en associant une catégorie au VSPackage qui le fournit. Prenons le fragment de code suivant :  
  
 [!code-csharp[VSSDKSupportForSettingsCategories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforsettingscategories/cs/vssdksupportforsettingscategoriespackage.cs#1)]
 [!code-vb[VSSDKSupportForSettingsCategories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforsettingscategories/vb/vssdksupportforsettingscategoriespackage.vb#1)]  
  
 L’ID de ressource 106 est mappé à « My Category », 107 à « My Settings » et 108 à « Various Options ». Cela déclare que `MyPackage` fournit la catégorie My Category_My Settings. La catégorie est fournie par la classe `OptionsPageGeneral`, qui doit implémenter <xref:Microsoft.VisualStudio.Shell.IProfileManager>. Les paramètres de cette catégorie sont les propriétés publiques de la classe `OptionsPageGeneral` .  
  
 Dans l’ **Assistant Importation et exportation de paramètres**, le point de paramètres se nomme My Settings. Quand le point de paramètres est sélectionné, la description, **Various Options**, s’affiche. Le nom et la description du point de paramètres sont extraits de ressources de chaînes localisées.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une Page d’Options](../extensibility/creating-an-options-page.md)   
 [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md)   
 [État du VSPackage](../misc/vspackage-state.md)   
 [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)