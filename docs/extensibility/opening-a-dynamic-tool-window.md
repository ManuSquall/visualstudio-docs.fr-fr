---
title: Ouverture d’une fenêtre outil dynamique | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d37a72629dfb7c10eeb51bcd2317151447e9edd
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636644"
---
# <a name="open-a-dynamic-tool-window"></a>Ouvrez une fenêtre d’outil dynamique
Fenêtres Outil sont généralement ouverts à partir d’une commande dans un menu ou un raccourci clavier équivalent. Dans certains cas, toutefois, vous devrez peut-être une fenêtre outil qui s’ouvre chaque fois qu’un contexte d’interface utilisateur spécifique s’applique et se ferme lorsque le contexte de l’interface utilisateur ne s’applique plus. Ces types de fenêtres Outil sont appelés *dynamique* ou *visibles automatiquement*.  
  
> [!NOTE]
>  Pour obtenir la liste des contextes d’interface utilisateur prédéfinis, consultez <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>.  
  
 Si vous souhaitez ouvrir une fenêtre d’outil dynamique au démarrage et il est possible de l’échec de la création, vous devez implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> d’interface et de tester les conditions d’échec dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> (méthode). Pour l’interpréteur de commandes que vous avez une fenêtre outil dynamique qui doit être ouvert au démarrage, vous devez ajouter le `SupportsDynamicToolOwner` valeur (1) pour l’inscription de votre package. Cette valeur ne fait pas partie de la norme <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, vous devez donc créer un attribut personnalisé pour l’ajouter. Pour plus d’informations sur les attributs personnalisés, consultez [utiliser un attribut personnalisé d’inscription pour inscrire une extension](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).  
  
 Utilisez <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> pour ouvrir une fenêtre outil. La fenêtre outil est créée en fonction des besoins.  
  
> [!NOTE]
>  Une fenêtre outil dynamique peut être fermée par l’utilisateur. Si vous souhaitez créer une commande de menu afin de l’utilisateur peut rouvrir la fenêtre outil, la commande de menu doit être activée dans le même contexte de l’interface utilisateur qui ouvre la fenêtre outil et désactivé dans le cas contraire.  
  
## <a name="to-open-a-dynamic-tool-window"></a>Pour ouvrir une fenêtre d’outil dynamique  
  
1.  Créez un projet VSIX nommé **DynamicToolWindow** et ajouter un modèle d’élément de fenêtre outil nommé *DynamicWindowPane.cs*. Pour plus d’informations, consultez [créer une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  Dans le *DynamicWindowPanePackage.cs* de fichier, recherchez la déclaration de DynamicWindowPanePackage. Ajouter le <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> et <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> attributs pour inscrire la fenêtre outil.  
  
    ```vb  
    [ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackage.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Les attributs ci-dessus s’inscrire à la fenêtre Outil nommée DynamicWindowPane sous forme de fenêtre temporaire qui n’est pas conservée lorsque Visual Studio est fermé et rouvert. DynamicWindowPane est ouvert chaque fois que <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> s’applique et fermés dans le cas contraire.  
  
3.  Générez le projet et commencez le débogage. L’instance expérimentale doit apparaître. Vous ne verrez pas la fenêtre outil.  
  
4.  Ouvrez un projet dans l’instance expérimentale. La fenêtre outil doit apparaître.