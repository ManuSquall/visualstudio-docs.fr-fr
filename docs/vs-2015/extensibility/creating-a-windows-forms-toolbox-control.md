---
title: Création d’un contrôle de boîte à outils Windows Forms | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 03fcc73c58baa1482c53e104a9946ffaa354f1a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698962"
---
# <a name="creating-a-windows-forms-toolbox-control"></a>Création d’un contrôle de boîte à outils Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le modèle d’élément de contrôle de boîte à outils Windows Forms inclus dans le Outils d’extensibilité de Visual Studio (kit de développement logiciel VS SDK) vous permet de créer un contrôle qui est automatiquement ajouté à la **boîte à outils** lorsque l’extension est installée. Cette rubrique montre comment utiliser le modèle pour créer un contrôle de compteur simple que vous pouvez distribuer à d’autres utilisateurs.  
  
## <a name="prerequisites"></a>Prérequis  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>Création d’un contrôle de boîte à outils Windows Forms  
 Le Windows Forms modèle de contrôle de boîte à outils crée un contrôle utilisateur non défini et fournit toutes les fonctionnalités nécessaires pour ajouter le contrôle à la **boîte à outils**.  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Créer une extension avec un contrôle de boîte à outils Windows Forms  
  
1. Créez un projet VSIX nommé `MyWinFormsControl` . Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** sous **Visual C#/extensibilité**.  
  
2. Lorsque le projet s’ouvre, ajoutez un Windows Forms modèle d’élément de **contrôle de boîte à outils** nommé `Counter` . Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter/nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à **Visual C#/extensibilité** et sélectionnez **Windows Forms contrôle de boîte à outils**  
  
3. Cela ajoute un contrôle utilisateur, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> pour placer le contrôle dans la **boîte à outils**et une entrée de ressource **Microsoft. VisualStudio. ToolboxControl** dans le manifeste VSIX pour le déploiement.  
  
### <a name="building-a-user-interface-for-the-control"></a>Création d’une interface utilisateur pour le contrôle  
 Le `Counter` contrôle requiert deux contrôles enfants : un <xref:System.Windows.Forms.Label> pour afficher le nombre actuel et un <xref:System.Windows.Forms.Button> pour réinitialiser le nombre à 0. Aucun autre contrôle enfant n’est nécessaire, car les appelants incrémentent le compteur par programmation.  
  
##### <a name="to-build-the-user-interface"></a>Pour créer l’interface utilisateur  
  
1. Dans **Explorateur de solutions**, double-cliquez sur Counter.cs pour l’ouvrir dans le concepteur.  
  
2. Supprimez le « cliquez ici ! » **Bouton** inclus par défaut lorsque vous ajoutez le modèle d’élément de contrôle Windows Forms boîte à outils.  
  
3. À partir de la **boîte à outils**, faites glisser un `Label` contrôle, puis un `Button` contrôle situé au-dessous de celui-ci vers l’aire de conception.  
  
4. Redimensionnez le contrôle utilisateur global sur 150, 50 pixels et redimensionnez le contrôle bouton sur 50, 20 pixels.  
  
5. Dans la fenêtre **Propriétés** , définissez les valeurs suivantes pour les contrôles sur l’aire de conception.  
  
    |Contrôler|Propriété|Valeur|  
    |-------------|--------------|-----------|  
    |`Label1`|**Text**|""|  
    |`Button1`|**Name**|btnReset|  
    |`Button1`|**Text**|Réinitialiser|  
  
### <a name="coding-the-user-control"></a>Codage du contrôle utilisateur  
 Le contrôle `Counter` expose une méthode pour incrémenter le compteur, un événement à déclencher chaque fois que le compteur est incrémenté, un bouton `Reset` et trois propriétés pour stocker le nombre actuel, stocker le texte affiché et indiquer s’il convient d’afficher ou de masquer le bouton `Reset` . L’attribut `ProvideToolboxControl` détermine l’emplacement dans la **boîte à outils** où le contrôle `Counter` s’affiche.  
  
##### <a name="to-code-the-user-control"></a>Pour coder le contrôle utilisateur  
  
1. Double-cliquez sur le formulaire pour ouvrir son gestionnaire d’événements de chargement dans la fenêtre de code.  
  
2. Au-dessus de la méthode de gestionnaire d’événements, dans la classe de contrôle, créez un entier pour stocker la valeur de compteur et une chaîne pour stocker le texte d’affichage comme indiqué dans l’exemple suivant.  
  
    ```csharp  
    int currentValue;  
    string displayText;  
    ```  
  
3. Créez les déclarations de propriété publiques suivantes.  
  
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
  
     Les appelants peuvent accéder à ces propriétés pour obtenir et définir le texte d’affichage du compteur et pour afficher ou masquer le `Reset` bouton. Les appelants peuvent obtenir la valeur actuelle de la propriété en lecture seule `Value` , mais ils ne peuvent pas définir la valeur directement.  
  
4. Placez le code suivant dans l' `Load` événement pour le contrôle.  
  
    ```csharp  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     La définition du texte de l' **étiquette** dans l' <xref:System.Windows.Forms.UserControl.Load> événement permet de charger les propriétés cibles avant que leurs valeurs ne soient appliquées. La définition du texte de l' **étiquette** dans le constructeur entraînerait une **étiquette**vide.  
  
5. Créez la méthode publique suivante pour incrémenter le compteur.  
  
    ```csharp  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6. Ajoutez une déclaration pour l' `Incremented` événement à la classe de contrôle.  
  
    ```csharp  
    public event EventHandler Incremented;  
    ```  
  
     Les appelants peuvent ajouter des gestionnaires à cet événement pour répondre aux modifications apportées à la valeur du compteur.  
  
7. Revenez en mode conception et double-cliquez sur le `Reset` bouton pour générer le `btnReset_Click` Gestionnaire d’événements, puis remplissez-le comme indiqué dans l’exemple suivant.  
  
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
  
### <a name="testing-the-control"></a>Test du contrôle  
 Pour tester un contrôle de **boîte à outils** , testez-le d’abord dans l’environnement de développement, puis testez-le dans une application compilée.  
  
##### <a name="to-test-the-control"></a>Pour tester le contrôle  
  
1. Appuyez sur F5.  
  
     Cela génère le projet et ouvre une deuxième instance expérimentale de Visual Studio sur laquelle le contrôle est installé.  
  
2. Dans l’instance expérimentale de Visual Studio, créez un projet d' **Application Windows Forms** .  
  
3. Dans **Explorateur de solutions**, double-cliquez sur Form1.cs pour l’ouvrir dans le concepteur s’il n’est pas déjà ouvert.  
  
4. Dans la **boîte à outils**, le `Counter` contrôle doit être affiché dans la section **général** .  
  
5. Faites glisser un `Counter` contrôle vers votre formulaire, puis sélectionnez-le. Les `Value` `Message` Propriétés, et `ShowReset` s’affichent dans la fenêtre **Propriétés** , ainsi que les propriétés héritées de <xref:System.Windows.Forms.UserControl> .  
  
6. Affectez à la propriété `Message` la valeur `Count:`.  
  
7. Faites glisser un <xref:System.Windows.Forms.Button> contrôle vers le formulaire, puis définissez les propriétés Name et Text du bouton sur `Test` .  
  
8. Double-cliquez sur le bouton pour ouvrir Form1.cs en mode Code et créer un gestionnaire de clics.  
  
9. Dans le gestionnaire de clic, appelez `counter1.Increment()` .  
  
10. Dans la fonction constructeur, après l’appel à `InitializeComponent` , tapez, `counter1``.``Incremented +=` puis appuyez deux fois sur la touche Tab.  
  
     Visual Studio génère un gestionnaire de niveau formulaire pour l' `counter1.Incremented` événement.  
  
11. Mettez en surbrillance l' `Throw` instruction dans le gestionnaire d’événements, tapez `mbox` , puis appuyez deux fois sur la touche Tab pour générer une boîte de message à partir de l’extrait de code mbox.  
  
12. Sur la ligne suivante, ajoutez le `if` / `else` bloc suivant pour définir la visibilité du `Reset` bouton.  
  
    ```csharp  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. Appuyez sur F5.  
  
     Le formulaire s’ouvre. Le `Counter` contrôle affiche le texte suivant.  
  
     **Nombre : 0**  
  
14. Cliquez sur **Test**.  
  
     Les incréments de compteur et Visual Studio affichent une boîte de message.  
  
15. Fermez la boîte de message.  
  
     Le bouton **Réinitialiser** disparaît.  
  
16. Cliquez sur **tester** jusqu’à ce que le compteur atteigne **5** fois la fermeture des boîtes de message.  
  
     Le bouton **Réinitialiser** s’affiche à nouveau.  
  
17. Cliquez sur **Réinitialiser**.  
  
     Le compteur se réinitialise à **0**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Quand vous générez un contrôle de **boîte à outils** , Visual Studio crée un fichier nommé *nom_projet*.vsix dans le dossier \bin\debug\ de votre projet. Vous pouvez déployer le contrôle en chargeant le fichier .vsix sur un réseau ou un site web. Quand un utilisateur ouvre le fichier. vsix, le contrôle est installé et ajouté à la **boîte à outils** Visual Studio sur l’ordinateur de l’utilisateur. Vous pouvez également télécharger le fichier. vsix sur le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) afin que les utilisateurs puissent le trouver en parcourant la boîte de dialogue **Outils/extension et mises à jour** .  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de la boîte à outils](../misc/extending-the-toolbox.md)   
 [Création d’un contrôle de boîte à outils WPF](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Extension d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Concepts de base du développement de contrôles Windows Forms](https://msdn.microsoft.com/library/6277bb81-90f7-4c5b-9f4b-b02bb42dd316)
