---
title: "Création d’une fenêtre d’outil multi-instance | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 12
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: bed04fe13e7232b2c227072ab91e6a56db0c6963
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="creating-a-multi-instance-tool-window"></a>Création d’une fenêtre d’outil à instances multiples
Vous pouvez programmer une fenêtre outil afin que plusieurs instances de celui-ci peuvent être ouverts simultanément. Par défaut, les fenêtres Outil peuvent ouvrir qu’une seule instance.  
  
 Lorsque vous utilisez une fenêtre d’outil à plusieurs instances, vous pouvez afficher plusieurs sources connexes d’informations en même temps. Par exemple, vous pouvez placer un multiligne <xref:System.Windows.Forms.TextBox> contrôle dans une fenêtre d’outil à plusieurs instances de sorte que plusieurs extraits de code sont disponibles simultanément pendant une session de programmation. Également par exemple, vous pouvez placer un <xref:System.Windows.Forms.DataGrid> contrôle et une liste déroulante de zone dans une fenêtre d’outil multi-instance afin que plusieurs sources de données en temps réel peuvent être suivis simultanément.  
  
## <a name="creating-a-basic-single-instance-tool-window"></a>Création d’une fenêtre d’outil Basic (SIS)  
  
1.  Créez un projet nommé **MultiInstanceToolWindow** à l’aide du modèle VSIX et ajouter un modèle d’élément de fenêtre outil personnalisé nommé **MIToolWindow**.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la création d’une extension avec une fenêtre outil, consultez [création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="making-a-tool-window-multi-instance"></a>Rendre une instance de multiples de fenêtre outil  
  
1.  Ouvrez le **MIToolWindowPackage.cs** de fichiers et recherchez le `ProvideToolWindow` attribut. et le `MultiInstances=true` paramètre, comme indiqué dans l’exemple suivant.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  Dans le fichier MIToolWindowCommand.cs, recherchez la méthode ShowToolWindos(). Dans cette méthode, appelez le <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> (méthode) et définissez son `create` indicateur `false` afin qu’il effectue une itération dans les instances de fenêtre Outil existantes jusqu'à un disponible `id` est trouvé.  
  
3.  Pour créer une instance de la fenêtre outil, appelez le <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> (méthode) et définissez son `id` à des valeurs disponibles et ses `create` indicateur `true`.  
  
     Par défaut, la valeur de la `id` paramètre de la <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> méthode est `0`. Cela rend une fenêtre outil à instance unique. Pour plus d’une instance doit être hébergé, chaque instance doit avoir son propre `id`.  
  
4.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> méthode sur le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objet qui est retourné par la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> propriété de l’instance de la fenêtre outil.  
  
5.  Par défaut, le `ShowToolWindow` méthode qui est créé par le modèle d’élément de fenêtre outil crée une fenêtre outil à instance unique. L’exemple suivant montre comment modifier le `ShowToolWindow` méthode pour créer plusieurs instances.  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```
