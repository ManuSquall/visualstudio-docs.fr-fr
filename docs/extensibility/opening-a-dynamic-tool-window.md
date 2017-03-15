---
title: "Ouverture d&#39;une fen&#234;tre outil dynamique | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fenêtres Outil, dynamiques"
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Ouverture d&#39;une fen&#234;tre outil dynamique
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Fenêtres Outil sont généralement ouvert à partir d'une commande dans un menu ou un raccourci clavier équivalent. Dans certains cas, toutefois, vous devrez peut\-être une fenêtre outil qui s'affiche chaque fois qu'un contexte de l'interface utilisateur spécifique s'applique et se ferme lorsque le contexte de l'interface utilisateur ne s'applique plus. Fenêtres Outil comme celles\-ci sont appelées *dynamique* ou *auto\-visible*.  
  
> [!NOTE]
>  Pour obtenir la liste des contextes d'interface utilisateur prédéfinies, consultez <xref:Microsoft.VisualStudio.VSConstants.UIContext>. Pour les  
  
 Si vous souhaitez ouvrir une fenêtre outil dynamique au démarrage et il est possible de l'échec de la création, vous devez implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> de l'interface et de tester les conditions d'échec de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> \(méthode\). Pour savoir que vous disposez d'une fenêtre outil dynamique qui doit être ouvert au démarrage de l'interpréteur de commandes, vous devez ajouter la `SupportsDynamicToolOwner` valeur \(1\) pour l'inscription du package. Cette valeur ne fait pas partie de la norme <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, vous devez donc créer un attribut personnalisé pour l'ajouter. Pour plus d'informations sur les attributs personnalisés, consultez la page [Utilisation d’un attribut d’inscription personnalisé pour inscrire une extension](/visual-cpp/misc/using-a-custom-registration-attribute-to-register-an-extension).  
  
 Utilisez <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> pour ouvrir une fenêtre outil. La fenêtre outil est créée en fonction des besoins.  
  
> [!NOTE]
>  Une fenêtre outil dynamique peut être fermée par l'utilisateur. Si vous souhaitez créer une commande de menu pour l'utilisateur peut rouvrir la fenêtre d'outils, la commande de menu doit être activée dans le même contexte de l'interface utilisateur qui ouvre la fenêtre outil et désactivée dans le cas contraire.  
  
### Pour ouvrir une fenêtre outil dynamique  
  
1.  Créez un projet VSIX nommé **DynamicToolWindow** et ajouter un modèle d'élément de fenêtre outil nommé **DynamicWindowPane.cs**. Pour plus d'informations, consultez [Création d'une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  Dans le fichier DynamicWindowPanePackage.cs, recherchez la déclaration de DynamicWindowPanePackage. Ajouter le <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> et les attributs T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute pour inscrire la fenêtre outil.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)] [PackageRegistration(UseManagedResourcesOnly = true)] [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About [ProvideMenuResource("Menus.ctmenu", 1)] [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))] [Guid(DynamicWindowPanePackageGuids.PackageGuidString)] public sealed class DynamicWindowPanePackage : Package {. . .}  
    ```  
  
     Cela permet d'enregistrer la fenêtre Outil nommée DynamicWindowPane sous forme de fenêtre temporaire qui n'est pas conservée lorsque Visual Studio est fermé et rouvert. DynamicWindowPane est ouvert chaque fois que <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> s'applique et fermés dans le cas contraire.  
  
3.  Générez le projet et commencez le débogage. L'instance expérimentale doit apparaître. Vous devez voir pas la fenêtre d'outils.  
  
4.  Ouvrez un projet dans l'instance expérimentale. La fenêtre outil doit apparaître.