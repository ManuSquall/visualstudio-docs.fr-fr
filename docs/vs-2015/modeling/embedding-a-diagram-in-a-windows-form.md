---
title: Incorporation d’un diagramme dans un formulaire Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6bd4117f3cce8a5a8a708da4b7941e224260ea15
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951612"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Incorporation d'un schéma dans un Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez incorporer un diagramme DSL dans un contrôle Windows, qui s’affiche dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fenêtre.  
  
## <a name="embedding-a-diagram"></a>Incorporation d’un diagramme  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Pour incorporer un diagramme DSL dans un contrôle Windows  
  
1.  Ajouter un nouveau **contrôle utilisateur** fichier au projet DslPackage.  
  
2.  Ajoutez un contrôle de panneau au contrôle utilisateur. Ce panneau contient le diagramme DSL.  
  
     Ajoutez des contrôles dont vous avez besoin.  
  
     Définissez les propriétés d’ancrage des contrôles.  
  
3.  Dans l’Explorateur de solutions, cliquez sur le fichier de contrôle utilisateur, puis cliquez sur **afficher le Code**. Ajouter ce constructeur et la variable au code :  
  
    ```csharp  
  
    internal UserControl1(MyDSLDocView docView, Control content)  
      : this()  
    {  
      panel1.Controls.Add(content);  
      this.docView = docView;  
    }  
    private MyDSLDSLDocView docView;  
  
    ```  
  
4.  Ajoutez un nouveau fichier au projet DslPackage, avec le contenu suivant :  
  
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
  
5.  Pour tester la solution DSL, appuyez sur F5 et ouvrir un exemple de fichier de modèle. Le diagramme apparaît à l’intérieur du contrôle. La boîte à outils et autres fonctionnalités fonctionnent normalement.  
  
#### <a name="updating-the-form-using-store-events"></a>La mise à jour le formulaire à l’aide d’événements de Store  
  
1.  Dans le Concepteur de formulaire, ajoutez un **ListBox** nommé `listBox1`. Cela affichera une liste des éléments dans le modèle. Il est conservé dans synchronism avec le modèle à l’aide *stocker les événements*. Pour plus d’informations, consultez [gestionnaires propager les modifications en dehors le modèle d’événement](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
2.  Dans le fichier de code personnalisé, substituez davantage les méthodes à la classe d’objet DocView :  
  
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
  
3.  Dans le code derrière le contrôle utilisateur, insérer des méthodes pour écouter les éléments ajoutés et supprimés :  
  
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
  
4.  Pour tester la solution DSL, appuyez sur F5 et dans l’instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ouvrez un exemple de fichier de modèle.  
  
     Notez que la zone de liste affiche une liste des éléments dans le modèle, et qu’il est correct après tout ajout ou la suppression et après les annuler et rétablir.  
  
## <a name="see-also"></a>Voir aussi  
 [Navigation et mise à jour d’un modèle dans le Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)
