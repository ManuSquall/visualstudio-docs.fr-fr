---
title: Incorporation d'un schéma dans un Windows Form
description: Découvrez comment vous pouvez incorporer un diagramme DSL dans un contrôle Windows, qui s’affiche dans la fenêtre Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4db60267b835882a69a08c990af644b902697bad
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388982"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Incorporer un diagramme dans un Windows Form

Vous pouvez incorporer un diagramme DSL dans un contrôle Windows, qui apparaît dans la fenêtre Visual Studio.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Incorporer un diagramme DSL dans un contrôle Windows

1. Ajoutez un nouveau fichier de **contrôle utilisateur** au projet DslPackage.

2. Ajoutez un contrôle de panneau au contrôle utilisateur. Ce panneau contiendra le diagramme DSL.

     Ajoutez d’autres contrôles dont vous avez besoin.

     Définissez les propriétés d’ancrage des contrôles.

3. Dans Explorateur de solutions, cliquez avec le bouton droit sur le fichier de contrôle utilisateur, puis cliquez sur **afficher le code**. Ajoutez ce constructeur et cette variable au code :

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4. Ajoutez un nouveau fichier au projet DslPackage, avec le contenu suivant :

    ```csharp
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

5. Pour tester le DSL, appuyez sur **F5** et ouvrez un exemple de fichier de modèle. Le diagramme s’affiche à l’intérieur du contrôle. La boîte à outils et d’autres fonctionnalités fonctionnent normalement.

## <a name="update-the-form-using-store-events"></a>Mettre à jour le formulaire à l’aide des événements Store

1. Dans le concepteur de formulaires, ajoutez une **zone de liste** nommée `listBox1` . Cette opération affiche une liste des éléments du modèle. Elle est synchronisée avec le modèle à l’aide d' *événements de magasin*. Pour plus d’informations, consultez les [gestionnaires d’événements propagent les modifications en dehors du modèle](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. Dans le fichier de code personnalisé, remplacez les autres méthodes de la classe DocView :

    ```csharp
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

3. Dans le code derrière le contrôle utilisateur, insérez les méthodes pour écouter les éléments ajoutés et supprimés :

    ```csharp
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

4. Pour tester le DSL, appuyez sur **F5** et, dans l’instance expérimentale de Visual Studio, ouvrez un exemple de fichier de modèle.

     Notez que la zone de liste affiche une liste des éléments dans le modèle, et qu’elle est correcte après l’ajout ou la suppression, et après les opérations d’annulation et de rétablissement.

## <a name="see-also"></a>Voir aussi

- [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)
