---
title: Incorporation d’un diagramme dans un Windows Form | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 487105350fe5c62a9451bccc5713c6506c76bf1f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669700"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Incorporation d'un schéma dans un Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez incorporer un diagramme DSL dans un contrôle Windows, qui apparaît dans la fenêtre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="embedding-a-diagram"></a>Incorporation d’un diagramme

#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Pour incorporer un diagramme DSL dans un contrôle Windows

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
    private MyDSLDSLDocView docView;

    ```

4. Ajoutez un nouveau fichier au projet DslPackage, avec le contenu suivant :

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

5. Pour tester le DSL, appuyez sur F5 et ouvrez un exemple de fichier de modèle. Le diagramme s’affiche à l’intérieur du contrôle. La boîte à outils et d’autres fonctionnalités fonctionnent normalement.

#### <a name="updating-the-form-using-store-events"></a>Mise à jour du formulaire à l’aide des événements Store

1. Dans le concepteur de formulaires, ajoutez une **zone de liste** nommée `listBox1`. Cette opération affiche une liste des éléments du modèle. Elle sera conservée synchronisée avec le modèle à l’aide d' *événements Store*. Pour plus d’informations, consultez les [gestionnaires d’événements propagent les modifications en dehors du modèle](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. Dans le fichier de code personnalisé, remplacez les autres méthodes de la classe DocView :

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

3. Dans le code derrière le contrôle utilisateur, insérez les méthodes pour écouter les éléments ajoutés et supprimés :

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

4. Pour tester le DSL, appuyez sur F5 et, dans l’instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ouvrez un exemple de fichier de modèle.

     Notez que la zone de liste affiche une liste des éléments dans le modèle, et qu’elle est correcte après l’ajout ou la suppression, et après les opérations d’annulation et de rétablissement.

## <a name="see-also"></a>Voir aussi
 [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md) [écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)
