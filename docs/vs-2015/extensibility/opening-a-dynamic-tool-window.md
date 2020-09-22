---
title: Ouverture d’une fenêtre outil dynamique | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09b81294abc708cf7616dad03b5dd7333d6a1719
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839897"
---
# <a name="opening-a-dynamic-tool-window"></a>Ouverture d’une fenêtre d’outil dynamique
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les fenêtres outil sont généralement ouvertes à partir d’une commande dans un menu ou d’un raccourci clavier équivalent. Toutefois, il peut arriver que vous ayez besoin d’une fenêtre outil qui s’ouvre chaque fois qu’un contexte d’interface utilisateur spécifique s’applique, et se ferme lorsque le contexte de l’interface utilisateur ne s’applique plus. Les fenêtres outil comme celles-ci sont appelées *Dynamic* ou *auto-visible*.  
  
> [!NOTE]
> Pour obtenir la liste des contextes d’interface utilisateur prédéfinis, consultez <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> . Pour le type de fichier  
  
 Si vous souhaitez ouvrir une fenêtre outil dynamique au démarrage et qu’il est possible que la création échoue, vous devez implémenter l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> interface et tester les conditions d’échec dans la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> méthode. Pour que l’interpréteur de commandes sache que vous disposez d’une fenêtre outil dynamique qui doit être ouverte au démarrage, vous devez ajouter la `SupportsDynamicToolOwner` valeur (définie sur 1) à l’inscription de votre package. Cette valeur ne fait pas partie de la norme <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> . vous devez donc créer un attribut personnalisé pour l’ajouter. Pour plus d’informations sur les attributs personnalisés, consultez [utilisation d’un attribut d’inscription personnalisé pour inscrire une extension](../misc/using-a-custom-registration-attribute-to-register-an-extension.md).  
  
 Utilisez <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> pour ouvrir une fenêtre outil. La fenêtre outil est créée en fonction des besoins.  
  
> [!NOTE]
> Une fenêtre outil dynamique peut être fermée par l’utilisateur. Si vous souhaitez créer une commande de menu afin que l’utilisateur puisse rouvrir la fenêtre outil, la commande de menu doit être activée dans le même contexte d’interface utilisateur qui ouvre la fenêtre outil, et désactivée dans le cas contraire.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Pour ouvrir une fenêtre outil dynamique  
  
1. Créez un projet VSIX nommé **DynamicToolWindow** et ajoutez un modèle d’élément de fenêtre outil nommé **DynamicWindowPane.cs**. Pour plus d’informations, consultez [création d’une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2. Dans le fichier DynamicWindowPanePackage.cs, recherchez la déclaration DynamicWindowPanePackage. Ajoutez les <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> attributs et T :Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute pour inscrire la fenêtre outil.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Cela enregistre la fenêtre outil nommée DynamicWindowPane comme une fenêtre temporaire qui n’est pas persistante lorsque Visual Studio est fermé et rouvert. DynamicWindowPane s’ouvre chaque fois que <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> s’applique, et est fermé dans le cas contraire.  
  
3. Générez le projet et commencez le débogage. L’instance expérimentale doit apparaître. Vous ne devriez pas voir la fenêtre outil.  
  
4. Ouvrez un projet dans l’instance expérimentale. La fenêtre outil doit s’afficher.
