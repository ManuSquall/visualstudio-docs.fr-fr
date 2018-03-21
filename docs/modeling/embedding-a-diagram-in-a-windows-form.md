---
title: "Incorporation d’un diagramme dans un Windows Form | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ab83ba64ff8b34c19e7f10aada74ca3eec1441f6
ms.sourcegitcommit: a80e7ef2f0a0f6d906a44f4d696aeb208bc1ad70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2018
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Incorporation d'un schéma dans un Windows Form
Vous pouvez incorporer un diagramme DSL dans un contrôle Windows, qui apparaît dans la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fenêtre.  
  
## <a name="embedding-a-diagram"></a>Incorporation d’un diagramme  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Pour incorporer un diagramme DSL dans un contrôle Windows  
  
1.  Ajouter un nouveau **contrôle utilisateur** fichier au projet DslPackage.  
  
2.  Ajouter un contrôle de panneau au contrôle utilisateur. Ce panneau contient le diagramme DSL.  
  
     Ajouter d’autres contrôles dont vous avez besoin.  
  
     Définir les propriétés d’ancrage des contrôles.  
  
3.  Dans l’Explorateur de solutions, cliquez sur le fichier de contrôle utilisateur, puis cliquez sur **afficher le Code**. Ajoutez ce constructeur et la variable au code :  
  
    ```csharp  
  
    internal UserControl1(MyDSLDocView docView, Control content)  
      : this()  
    {  
      panel1.Controls.Add(content);  
      this.docView = docView;  
    }  
    private MyDSLDocView docView;  
  
    ```  
  
4.  Ajouter un nouveau fichier au projet DslPackage, avec le contenu suivant :  
  
    ```  
    using System.Windows.Forms;  
    namespace Company.MyDSL  
    {  
      partial class MyDSLDocView  
      {  
        private UserControl1 container;  
        public override IWin32Window Window  
        {  
          get  
          {  
            if (container == null)  
            {  
              // Put our own form inside the DSL window:  
              container = new UserControl1(this,  
                (Control)base.Window);  
            }  
            return container;  
    } } } }  
  
    ```  
  
5.  Pour tester la DSL, appuyez sur F5 et ouvrir un exemple de fichier de modèle. Le diagramme s’affiche dans le contrôle. La boîte à outils et autres fonctionnalités fonctionnent normalement.  
  
#### <a name="updating-the-form-using-store-events"></a>Mise à jour de l’écran à l’aide d’événements de la banque  
  
1.  Dans le Concepteur de formulaire, ajoutez un **ListBox** nommé `listBox1`. Cela affiche une liste des éléments dans le modèle. Il est conservé dans synchronism avec le modèle à l’aide de *stocker les événements*. Pour plus d’informations, consultez [gestionnaires propager les modifications en dehors du modèle d’événement](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
2.  Dans le fichier de code personnalisé, substituez davantage les méthodes à la classe DocView :  
  
    ```  
  
    partial class MyDSLDocView  
    {  
     /// <summary>  
     /// Register store event listeners.  
     /// This method is called when the model and diagram    
     /// have completed loading.   
     /// </summary>  
     protected override bool LoadView()  
      {  
        bool result = base.LoadView();  
        Store store = this.DocData.Store;  
        EventManagerDirectory emd = store.EventManagerDirectory;  
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));  
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));  
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));  
  
        // Do the initial parts list:  
        container.SetUpFormFromModel();  
        return result;  
      }  
     /// <summary>  
     /// Listener method called on creation of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void AddElement(object sender, ElementAddedEventArgs e)  
     {  
       container.Add(e.ModelElement as ExampleElement);  
     }  
     /// <summary>  
     /// Listener method called after deletion of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void RemoveElement(object sender, ElementDeletedEventArgs e)  
     {  
       container.Remove(e.ModelElement as ExampleElement);  
     }  
  
    ```  
  
3.  Dans le code derrière le contrôle utilisateur, insérer les méthodes pour écouter les éléments ajoutés et supprimés :  
  
    ```  
  
          public partial class UserControl1 : UserControl { ...  
  
    private ExampleModel modelRoot;  
  
    internal void Add(ExampleElement e) { UpdatePartsList(); }  
    internal void Remove(ExampleElement e) { UpdatePartsList(); }  
  
    internal void SetUpFormFromModel()  
    {  
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;  
      UpdatePartsList();  
    }  
  
    private void UpdatePartsList()  
    {  
      StringBuilder builder = new StringBuilder();  
      listBox1.Items.Clear();  
      foreach (ExampleElement c in modelRoot.Elements)  
      {  
        listBox1.Items.Add(c.Name);  
      }  
    }  
  
    ```  
  
4.  Pour tester la DSL, appuyez sur F5 et dans l’instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ouvrez un exemple de fichier de modèle.  
  
     Notez que la zone de liste affiche une liste des éléments dans le modèle, et qu’elle est correcte après l’ajout ou la suppression et après avoir Annuler et rétablir.  
  
## <a name="see-also"></a>Voir aussi  
 [Navigation et la mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)
