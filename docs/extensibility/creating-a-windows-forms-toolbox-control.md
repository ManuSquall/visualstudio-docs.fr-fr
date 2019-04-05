---
title: Création d’un Windows Forms de contrôle de boîte à outils | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3c423361b860c5769d9555409b44973fdc25896
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194575"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Créer un contrôle de boîte à outils Windows Forms

Le modèle d’élément de contrôle de boîte à outils Windows Forms qui est inclus dans les outils d’extensibilité de Visual Studio (Visual Studio SDK), vous permet de créer un **boîte à outils** contrôle qui est ajouté automatiquement lorsque l’extension est installée. Cette procédure pas à pas montre comment utiliser le modèle pour créer un contrôle simple compteur que vous pouvez distribuer à d’autres utilisateurs.

## <a name="prerequisites"></a>Prérequis

À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Créer le contrôle de boîte à outils

Le modèle de contrôle de boîte à outils Windows Forms crée un contrôle utilisateur non défini et fournit toutes les fonctionnalités requises pour ajouter le contrôle à la **boîte à outils**.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Créer une extension avec un contrôle de boîte à outils Windows Forms

1. Créez un projet VSIX nommé `MyWinFormsControl`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue, en recherchant « vsix ».

2. Quand le projet s’ouvre, ajoutez un **contrôle de boîte à outils Windows Forms** modèle d’élément nommé `Counter`. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **ajouter** > **un nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual C#** > **extensibilité** et sélectionnez **contrôle de boîte à outils Windows Forms**

3. Cette opération ajoute un contrôle utilisateur, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> pour placer le contrôle dans le **boîte à outils**et un **Microsoft.VisualStudio.ToolboxControl** l’entrée de composant dans le manifeste VSIX pour le déploiement.

### <a name="build-a-user-interface-for-the-control"></a>Créer une interface utilisateur pour le contrôle

Le `Counter` contrôle requiert deux contrôles enfants : un <xref:System.Windows.Forms.Label> pour afficher le nombre actuel et un <xref:System.Windows.Forms.Button> pour réinitialiser le nombre sur 0. Aucun autre contrôle enfant n’est requis, car les appelants incrémente le compteur par programmation.

#### <a name="to-build-the-user-interface"></a>Pour créer l’interface utilisateur

1. Dans **l’Explorateur de solutions**, double-cliquez sur *Counter.cs* pour l’ouvrir dans le concepteur.

2. Supprimer le **cliquez ici !** bouton qui est inclus par défaut lorsque vous ajoutez le modèle d’élément de contrôle de boîte à outils Windows Forms.

3. À partir de la **boîte à outils**, faites glisser un `Label` contrôle, puis un `Button` contrôle en dessous de l’aire de conception.

4. Redimensionnez le contrôle utilisateur global à 150, 50 pixels et redimensionnez le bouton de contrôle à 50, 20 pixels.

5. Dans le **propriétés** fenêtre, définissez les valeurs suivantes pour les contrôles sur l’aire de conception.

    |Contrôle|Propriété|Value|
    |-------------|--------------|-----------|
    |`Label1`|**Text**|""|
    |`Button1`|**Name**|btnReset|
    |`Button1`|**Text**|Réinitialiser|

### <a name="code-the-user-control"></a>Coder le contrôle utilisateur

Le `Counter` contrôle expose une méthode pour incrémenter le compteur, un événement à déclencher chaque fois que le compteur est incrémenté, un **réinitialiser** bouton et trois propriétés pour stocker le nombre actuel, le texte affiché et s’il faut afficher ou masquer la **réinitialiser** bouton. L’attribut `ProvideToolboxControl` détermine l’emplacement dans la **boîte à outils** où le contrôle `Counter` s’affiche.

#### <a name="to-code-the-user-control"></a>Pour coder le contrôle utilisateur

1. Double-cliquez sur le formulaire pour ouvrir son gestionnaire d’événements load dans la fenêtre de code.

2. Au-dessus de la méthode de gestionnaire d’événements, dans la classe de contrôle, créez un entier pour stocker la valeur du compteur et une chaîne pour stocker le texte à afficher comme indiqué dans l’exemple suivant.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Créer les déclarations suivantes de la propriété publique.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    Les appelants peuvent accéder à ces propriétés pour obtenir et définir le texte d’affichage du compteur et pour afficher ou masquer la **réinitialiser** bouton. Les appelants peuvent obtenir la valeur actuelle de la lecture seule `Value` propriété, mais ils ne peuvent pas définir directement la valeur.

4. Placez le code suivant le `Load` événement pour le contrôle.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Définition de la **étiquette** texte dans le <xref:System.Windows.Forms.UserControl.Load> événement Active les propriétés de cible charger avant que leurs valeurs soient appliquées. Définition de la **étiquette** vide entraînerait le texte dans le constructeur **étiquette**.

5. Créez la méthode publique suivante pour incrémenter le compteur.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Ajoutez une déclaration pour le `Incremented` événement à la classe de contrôle.

    ```csharp
    public event EventHandler Incremented;
    ```

    Les appelants peuvent ajouter des gestionnaires à cet événement pour répondre aux modifications de la valeur du compteur.

7. Revenez à la vue de conception et double-cliquez sur le **réinitialiser** bouton pour générer le `btnReset_Click` Gestionnaire d’événements et le remplir dans comme illustré dans l’exemple suivant.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Immédiatement au-dessus de la définition de classe, dans la déclaration d’attribut `ProvideToolboxControl` , remplacez la valeur `"MyWinFormsControl.Counter"` du premier paramètre par `"General"`. Le nom du groupe d’éléments qui va héberger le contrôle dans la **boîte à outils**est ainsi défini.

    L’exemple suivant illustre l’attribut `ProvideToolboxControl` et la définition de classe ajustée.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Tester le contrôle

 Pour tester un **boîte à outils** contrôler, testez-le d’abord dans l’environnement de développement et à le tester dans une application compilée.

#### <a name="to-test-the-control"></a>Pour tester le contrôle

1. Appuyez sur **F5** à **démarrer le débogage**.

    Cette commande génère le projet et ouvre une deuxième instance expérimentale de Visual Studio qui a le contrôle est installé.

2. Dans l’instance expérimentale de Visual Studio, créez un **Windows Forms Application** projet.

3. Dans **l’Explorateur de solutions**, double-cliquez sur *Form1.cs* pour l’ouvrir dans le concepteur s’il n’est pas déjà ouvert.

4. Dans le **boîte à outils**, le `Counter` contrôle doit être affiché dans le **général** section.

5. Faites glisser un `Counter` le contrôle à votre formulaire, puis sélectionnez-le. Le `Value`, `Message`, et `ShowReset` propriétés seront affichera dans le **propriétés** fenêtre, ainsi que les propriétés qui sont héritées de <xref:System.Windows.Forms.UserControl>.

6. Affectez à la propriété `Message` la valeur `Count:`.

7. Faites glisser un <xref:System.Windows.Forms.Button> au formulaire, puis définissez les propriétés de nom et le texte du bouton sur `Test`.

8. Double-cliquez sur le bouton pour ouvrir *Form1.cs* en mode code et créer un gestionnaire de clic.

9. Dans le Gestionnaire de clic, appelez `counter1.Increment()`.

10. Dans la fonction constructeur, après l’appel à `InitializeComponent`, type `counter1``.``Incremented +=` , puis appuyez sur **onglet** à deux reprises.

    Visual Studio génère un gestionnaire au niveau du formulaire pour le `counter1.Incremented` événement.

11. Mettez en surbrillance le `Throw` instruction dans le Gestionnaire d’événements, type `mbox`, puis appuyez sur **onglet** à deux reprises pour générer une boîte de message à partir de l’extrait de code mbox.

12. Sur la ligne suivante, ajoutez le code suivant `if` / `else` bloc pour définir la visibilité de la **réinitialiser** bouton.

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Appuyez sur **F5**.

    Le formulaire s’ouvre. Le `Counter` contrôle affiche le texte suivant.

    **Nombre : 0**

14. Cliquez sur **Test**.

    Le compteur s’incrémente et Visual Studio affiche une boîte de message.

15. Fermez la boîte de message.

    Le **réinitialiser** bouton disparaît.

16. Cliquez sur **Test** jusqu'à ce que le compteur atteint **5** fermer le message boîtes à chaque fois.

    Le **réinitialiser** bouton s’affiche de nouveau.

17. Cliquez sur **Réinitialiser**.

    Le compteur est remis à **0**.

## <a name="next-steps"></a>Étapes suivantes

Lorsque vous générez un **boîte à outils** (contrôle), Visual Studio crée un fichier nommé *ProjectName.vsix* dans le dossier \bin\debug\ de votre projet. Vous pouvez déployer le contrôle en chargeant le *.vsix* fichier à un réseau ou à un site Web. Lorsqu’un utilisateur ouvre le *.vsix* , le contrôle est installé et ajouté à Visual Studio **boîte à outils** sur l’ordinateur de l’utilisateur. Ou bien, vous pouvez télécharger le *.vsix* fichier [Visual Studio Marketplace](https://marketplace.visualstudio.com/) afin que les utilisateurs puissent le trouver en naviguant dans le **outils**  >   **Extensions et mises à jour** boîte de dialogue.

## <a name="see-also"></a>Voir aussi

- [Étendre d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Créer un contrôle de boîte à outils WPF](../extensibility/creating-a-wpf-toolbox-control.md)
- [Étendre d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Concepts de base développement de contrôles Windows Forms](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
