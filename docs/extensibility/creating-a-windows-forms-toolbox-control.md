---
title: Création d’un contrôle de boîte à outils Windows Forms (fr) Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7e7749302252c5d56f21c58de9b6ac23f898572
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739584"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Créer un contrôle windows Forme boîte à outils

Le modèle d’élément de contrôle de boîte à outils Windows Forms qui est inclus dans les outils d’exté sensibilité Visual Studio (VS SDK), vous permet de créer un contrôle **De boîte à outils** qui est automatiquement ajouté lorsque l’extension est installée. Ce pas-là montre comment utiliser le modèle pour créer un contrôle de compteur simple que vous pouvez distribuer à d’autres utilisateurs.

## <a name="prerequisites"></a>Prérequis

A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Créer le contrôle de la boîte à outils

Le modèle de contrôle de boîte à outils Windows Forms crée un contrôle indéfini de l’utilisateur et fournit toutes les fonctionnalités nécessaires pour ajouter le contrôle à la boîte à **outils**.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Créez une extension avec un contrôle windows Forms Toolbox

1. Créer un projet `MyWinFormsControl`VSIX nommé . Vous pouvez trouver le modèle de projet VSIX dans le dialogue **du nouveau projet,** en recherchant "vsix".

2. Lorsque le projet s’ouvre, ajoutez un modèle **d’élément de contrôle de boîte à** outils Windows Forms nommé `Counter`. Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Dans le dialogue **Add New Item,** rendez-vous sur Visual C **'Extensibility** **Visual C#** > et sélectionnez **Windows Forms Toolbox Control**

3. Cela ajoute un contrôle `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> utilisateur, un pour placer le contrôle dans la boîte à **outils**, et une entrée **Microsoft.VisualStudio.ToolboxControl** Asset dans le manifeste VSIX pour le déploiement.

### <a name="build-a-user-interface-for-the-control"></a>Construire une interface utilisateur pour le contrôle

Le `Counter` contrôle nécessite deux <xref:System.Windows.Forms.Label> contrôles pour enfants : <xref:System.Windows.Forms.Button> un pour afficher le nombre actuel, et un pour réinitialiser le compte à 0. Aucun autre contrôle des enfants n’est nécessaire parce que les appelants incrémentent le compteur de façon programmatique.

#### <a name="to-build-the-user-interface"></a>Pour créer l’interface utilisateur

1. Dans **Solution Explorer**, double clic *Counter.cs* de l’ouvrir dans le concepteur.

2. Supprimer le **clic ici !** bouton qui est inclus par défaut lorsque vous ajoutez le modèle d’élément de contrôle de boîte à outils Windows Forms.

3. De la **boîte à outils**, faire glisser un `Label` contrôle, puis un `Button` contrôle en dessous à la surface de conception.

4. Resize le contrôle global de l’utilisateur à 150, 50 pixels, et resize le contrôle du bouton à 50, 20 pixels.

5. Dans la fenêtre **Propriétés,** définissez les valeurs suivantes pour les commandes sur la surface de conception.

    |Control|Propriété|Valeur|
    |-------------|--------------|-----------|
    |`Label1`|**Text**|""|
    |`Button1`|**Nom**|btnReset (en)|
    |`Button1`|**Text**|Réinitialiser|

### <a name="code-the-user-control"></a>Codez le contrôle de l’utilisateur

Le `Counter` contrôle exposera une méthode pour incrémenter le compteur, un événement à soulever chaque fois que le compteur est incrémenté, un bouton **Reset,** et trois propriétés pour stocker le nombre actuel, le texte d’affichage, et s’il faut afficher ou cacher le bouton **Reset.** L’attribut `ProvideToolboxControl` détermine l’emplacement dans la **boîte à outils** où le contrôle `Counter` s’affiche.

#### <a name="to-code-the-user-control"></a>Pour coder le contrôle de l’utilisateur

1. Double-cliquez sur le formulaire pour ouvrir son gestionnaire d’événement de charge dans la fenêtre de code.

2. Au-dessus de la méthode du gestionnaire d’événements, dans la classe de contrôle créer un intégriste pour stocker la valeur du comptoir et une chaîne pour stocker le texte d’affichage comme indiqué dans l’exemple suivant.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Créez les déclarations de propriété publique suivantes.

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

    Les appelants peuvent accéder à ces propriétés pour obtenir et définir le texte d’affichage du compteur et pour afficher ou masquer le bouton **Reset.** Les appelants peuvent obtenir la valeur `Value` actuelle de la propriété de lecture seulement, mais ils ne peuvent pas définir la valeur directement.

4. Mettez le code `Load` suivant dans l’événement pour le contrôle.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    La **Label** définition du <xref:System.Windows.Forms.UserControl.Load> texte Label dans l’événement permet aux propriétés cibles de se charger avant que leurs valeurs ne soient appliquées. La définition du texte **d’étiquette** dans le constructeur entraînerait une **étiquette**vide.

5. Créez la méthode publique suivante pour incrémenter le compteur.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Ajoutez une déclaration `Incremented` pour l’événement à la classe de contrôle.

    ```csharp
    public event EventHandler Incremented;
    ```

    Les appelants peuvent ajouter des gestionnaires à cet événement pour répondre aux changements dans la valeur du compteur.

7. Retournez à la vue **Reset** de conception et `btnReset_Click` double-cliquez sur le bouton Reset pour générer le gestionnaire d’événement, puis remplissez-le comme indiqué dans l’exemple suivant.

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

 Pour tester un contrôle **de boîte à outils,** d’abord le tester dans l’environnement de développement, puis le tester dans une application compilée.

#### <a name="to-test-the-control"></a>Pour tester le contrôle

1. Appuyez **sur F5** pour **commencer à débugging**.

    Cette commande construit le projet et ouvre une deuxième instance expérimentale de Visual Studio qui a le contrôle installé.

2. Dans l’exemple expérimental de Visual Studio, créez un projet **d’application Windows Forms.**

3. Dans **Solution Explorer**, double-clic *Form1.cs* de l’ouvrir dans le concepteur si elle n’est pas déjà ouverte.

4. Dans la boîte `Counter` à **outils,** le contrôle doit être affiché dans la section **Générale.**

5. Faites `Counter` glisser un contrôle sur votre formulaire, puis sélectionnez-le. Le `Value` `Message`, `ShowReset` , et les propriétés seront affichées dans la <xref:System.Windows.Forms.UserControl>fenêtre **Propriétés,** ainsi que les propriétés qui sont héritées de .

6. Attribuez à la propriété `Message` la valeur `Count:`.

7. Faites <xref:System.Windows.Forms.Button> glisser un contrôle sur le formulaire, puis définissez `Test`les propriétés nom et texte du bouton à .

8. Double-cliquez sur le bouton pour ouvrir *Form1.cs* en vue de code et créer un gestionnaire de clics.

9. Dans le gestionnaire `counter1.Increment()`de clic, appelez .

10. Dans la fonction constructeur, après `InitializeComponent`l’appel à , tapez, `counter1``.``Incremented +=` puis appuyez sur **Tab** deux fois.

    Visual Studio génère un gestionnaire de `counter1.Incremented` niveau de forme pour l’événement.

11. Mettez `Throw` en évidence la déclaration `mbox`dans le gestionnaire d’événement, tapez, puis appuyez sur **Tab** deux fois pour générer une boîte de message à partir de l’extrait de code mbox.

12. Sur la ligne suivante, `if` / `else` ajoutez le bloc suivant pour définir la visibilité du bouton **Reset.**

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Appuyez sur **F5**.

    Le formulaire s’ouvre. Le `Counter` contrôle affiche le texte suivant.

    **Nombre: 0**

14. Cliquez sur **Test**.

    Les incréments de compteur et Visual Studio affiche une boîte de message.

15. Fermez la boîte à messages.

    Le bouton **Reset** disparaît.

16. Cliquez **sur Test** jusqu’à ce que le compteur atteigne **5** fermant les boîtes de messages à chaque fois.

    Le bouton **Reset** réapparaît.

17. Cliquez sur **Réinitialiser**.

    Le compteur se réinitialise à **0**.

## <a name="next-steps"></a>Étapes suivantes

Lorsque vous construisez un contrôle **Toolbox,** Visual Studio crée un fichier nommé *ProjectName.vsix* dans le dossier 'bin’debug' de votre projet. Vous pouvez déployer le contrôle en téléchargeant le fichier *.vsix* sur un réseau ou sur un site Web. Lorsqu’un utilisateur ouvre le fichier *.vsix,* le contrôle est installé et ajouté à la boîte à **outils** Visual Studio sur l’ordinateur de l’utilisateur. Alternativement, vous pouvez télécharger le fichier *.vsix* sur [Visual Studio Marketplace](https://marketplace.visualstudio.com/) afin que les utilisateurs puissent le trouver en naviguant dans les **extensions d’outils** > **et de updates** dialogue.

## <a name="see-also"></a>Voir aussi

- [Étendre d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Créez un contrôle de boîte à outils WPF](../extensibility/creating-a-wpf-toolbox-control.md)
- [Étendre d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Windows Forms contrôle les bases du développement](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
