---
title: Mettre à jour un modèle UML à partir d’un thread d’arrière-plan | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cd0707ec7838ffb2dcebc8a176c79810f2614133
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953187"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>Mettre à jour un modèle UML à partir d'un thread d'arrière-plan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il peut parfois être utile apporter des modifications à un modèle dans un thread d'arrière-plan. Par exemple, si vous chargez des informations à partir d'une ressource externe lente, vous pouvez utiliser un thread d'arrière-plan pour superviser les mises à jour. Cela permet à l'utilisateur de voir chaque mise à jour dès qu'elle a lieu.  
  
 Toutefois, vous devez savoir que le magasin UML n'est pas thread-safe. Les précautions suivantes sont importantes :  
  
-   Chaque mise à jour d'un modèle ou d'un diagramme doit être effectuée dans le thread d'interface utilisateur. Le thread d'arrière-plan doit utiliser <xref:System.Windows.Forms.Control.Invoke%2A> ou `Dispatcher.`<xref:System.Windows.Threading.Dispatcher.Invoke%2A> pour que le thread d'interface utilisateur effectue réellement les mises à jour.  
  
-   Si vous regroupez une série de modifications dans une transaction unique, nous vous recommandons d'empêcher l'utilisateur de modifier le modèle pendant que la transaction est en cours. Autrement, les modifications apportées par l'utilisateur feront partie de la même transaction. Vous pouvez empêcher l'utilisateur d'apporter des modifications en affichant une boîte de dialogue modale. Si vous le souhaitez, vous pouvez fournir un bouton Annuler dans la boîte de dialogue. L'utilisateur peut voir les modifications à mesure qu'elles se produisent.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise un thread d'arrière-plan pour apporter plusieurs modifications à un modèle. Une boîte de dialogue permet d'exclure l'utilisateur pendant que le thread s'exécute. Dans cet exemple simple, la boîte de dialogue ne contient pas de bouton Annuler. Toutefois, il serait facile d'ajouter cette fonctionnalité.  
  
#### <a name="to-run-the-example"></a>Pour exécuter l'exemple  
  
1. Créez un gestionnaire de commandes dans un projet c#, comme décrit dans [définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
2. Assurez-vous que le projet comprend des références aux assemblys suivants :  
  
   -   Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.[version]  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]  
  
   -   Microsoft.VisualStudio.Uml.Interfaces  
  
   -   System.ComponentModel.Composition  
  
   -   System.Windows.Forms  
  
3. Ajoutez au projet un formulaire Windows nommé **ProgressForm**. Il doit afficher un message indiquant que les mises à jour sont en cours. Il n'est pas nécessaire qu'il contienne d'autres contrôles.  
  
4. Ajoutez un fichier C# qui contient le code indiqué après l'étape 7.  
  
5. Générez et exécutez le projet.  
  
    Une nouvelle instance de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] démarre en mode expérimental.  
  
6. Créez ou ouvrez un diagramme de classes UML dans l'instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7. Avec le bouton droit n’importe où dans le diagramme de classes UML, puis cliquez sur **ajouter plusieurs Classes UML**.  
  
   Plusieurs nouvelles zones de classes sont affichées dans le diagramme, l'une après l'autre à des intervalles d'une demi-seconde.  
  
```csharp  
using System;  
using System.ComponentModel;  
using System.ComponentModel.Composition;  
using System.Threading;  
using System.Windows.Forms;  
  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.Uml.Classes;  
  
namespace BackgroundThreadProgressUI // CHANGE TO YOUR NAMESPACE  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  class UmlClassAdderCommand : ICommandExtension  
  {  
  
    [Import]  
    IDiagramContext context { get; set; }  
  
    [Import]  
    ILinkedUndoContext linkedUndoContext { get; set; }  
  
    // Called when the user runs the command.  
    public void Execute(IMenuCommand command)  
    {  
      // The form that will exclude the user.  
      ProgressForm form = new ProgressForm();  
  
      // System.ComponentModel.BackgroundWorker is a  
      // convenient way to run a background thread.  
      BackgroundWorker worker = new BackgroundWorker();  
      worker.WorkerSupportsCancellation = true;  
  
      worker.DoWork += delegate(object sender, DoWorkEventArgs args)  
      {  
        // This block will be executed in a background thread.  
  
        IClassDiagram diagram = context.CurrentDiagram as IClassDiagram;  
        IModelStore store = diagram.ModelStore;  
        const int CLASSES_TO_CREATE = 15;  
  
        // Group all the changes together.  
        using (ILinkedUndoTransaction transaction = linkedUndoContext.BeginTransaction("Background Updates"))  
        {  
          for (int i = 1; i < CLASSES_TO_CREATE; i++)  
          {  
            if (worker.CancellationPending)   
               return; // No commit - undo all.  
  
            // Create model elements using the UI thread by using  
            // the Invoke method on the progress form. Always   
            // modify the model and diagrams from a UI thread.  
            form.Invoke((MethodInvoker)(delegate  
            {  
              IClass newClass = store.Root.CreateClass();  
              newClass.Name = string.Format("NewClass{0}", i);  
              diagram.Display(newClass);  
            }));  
  
            // Sleep briefly so that we can watch the updates.  
            Thread.Sleep(500);  
          }  
  
          // Commit the transaction or it will be rolled back.  
          transaction.Commit();  
        }  
      };  
  
      // Close the form when the thread completes.  
      worker.RunWorkerCompleted += delegate(object sender, RunWorkerCompletedEventArgs args)  
      {  
        form.Close();  
      };  
  
      // Start the thread before showing the modal progress dialog.  
      worker.RunWorkerAsync();  
  
      // Show the form modally, parented on VS.  
      // Prevents the user from making changes while in progress.  
      form.ShowDialog();  
    }  
  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
  
    public string Text  
    {  
      get { return "Add several classes"; }  
    }  
  }  
}  
```  
  
#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>Pour permettre à l'utilisateur d'annuler le thread dans l'exemple  
  
1.  Ajoutez un bouton Annuler à la boîte de dialogue de progression.  
  
2.  Ajoutez le code suivant à la boîte de dialogue de progression :  
  
     `public event MethodInvoker Cancel;`  
  
     `private void CancelButton_Click(object sender, EventArgs e)`  
  
     `{`  
  
     `Cancel();`  
  
     `}`  
  
3.  Dans la méthode Execute(), insérez cette ligne après la construction du formulaire :  
  
     `form.Cancel += delegate() { worker.CancelAsync(); };`  
  
### <a name="other-methods-of-accessing-the-ui-thread"></a>Autres méthodes d'accès au thread d'interface utilisateur  
 Si vous ne souhaitez pas créer de boîte de dialogue, vous pouvez accéder au contrôle qui affiche le diagramme :  
  
 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`  
  
 Vous pouvez utiliser `uiThreadHolder.Invoke()` pour effectuer des opérations dans le thread d'interface utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Définir un gestionnaire de mouvements sur un diagramme de modélisation](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)
