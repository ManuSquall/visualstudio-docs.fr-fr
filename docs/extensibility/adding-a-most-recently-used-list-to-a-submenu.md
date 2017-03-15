---
title: "Ajout d&#39;une plus r&#233;cemment utilis&#233;s &#224; un sous-menu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "listes utilisées récemment"
  - "menus, création de la liste des derniers fichiers utilisés"
  - "utilisés le plus récemment"
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 46
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 46
---
# Ajout d&#39;une plus r&#233;cemment utilis&#233;s &#224; un sous-menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas s'appuie sur des démonstrations de [Ajout d'un sous\-menu à un Menu](../extensibility/adding-a-submenu-to-a-menu.md), et montre comment ajouter une liste dynamique à un sous\-menu. La liste dynamique constitue la base pour la création d'une liste plus récemment utilisés \(MRU\).  
  
 Une liste de menu dynamique commence par un espace réservé dans un menu. Chaque fois que le menu est affiché, l'environnement de développement intégré \(IDE\) Visual Studio vous demande le VSPackage pour toutes les commandes qui doivent être affichées à l'espace réservé. Une liste dynamique peut se produire n'importe où dans un menu. Toutefois, les listes dynamiques sont généralement stockés et affichés par eux\-mêmes de sous\-menus ou au bas des menus. À l'aide de ces modèles de conception, vous activez la liste des commandes pour développer et réduire sans modifier la position d'autres commandes du menu dynamique. Dans cette procédure pas à pas, la liste des derniers fichiers utilisés est affichée en bas d'un sous\-menu existant, séparé du reste du sous\-menu par une ligne.  
  
 Techniquement, une liste dynamique peut également être appliquée à une barre d'outils. Toutefois, nous déconseillons cette utilisation car une barre d'outils doit rester inchangé, sauf si l'utilisateur prend des mesures spécifiques pour le modifier.  
  
 Cette procédure pas à pas crée une liste de quatre éléments qui modifient leur ordre chaque fois qu'un d'entre eux est sélectionné \(l'élément sélectionné se déplace vers le haut de la liste\).  
  
 Pour plus d'informations sur les menus et les fichiers .vsct, consultez la page [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## Composants requis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel \(SDK\) Visual Studio. Pour plus d'informations, consultez [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Création d'une Extension  
  
-   Suivez les procédures de [Ajout d'un sous\-menu à un Menu](../extensibility/adding-a-submenu-to-a-menu.md) pour créer le sous\-menu est modifié dans les procédures suivantes.  
  
 Les procédures décrites dans cette procédure pas à pas supposent que le nom du package VS est `TopLevelMenu`, qui est le nom utilisé dans [Ajout d'un Menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## Création d'une commande de la liste élément dynamique  
  
1.  Ouvrez TestCommandPackage.vsct.  
  
2.  Dans la `Symbols` section, dans le `GuidSymbol` nœud nommé guidTestCommandPackageCmdSet, ajoutez le symbole pour le `MRUListGroup` groupe et `cmdidMRUList` commande, comme suit.  
  
    ```c#  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  Dans la `Groups` section, ajoutez le groupe déclaré après les entrées de groupe existant.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  Dans la `Buttons` ajoutez un nœud pour représenter la commande qui vient d'être déclarée, après les entrées du bouton existant.  
  
    ```c#  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     Le `DynamicItemStart` l'indicateur permet à la commande pour être généré dynamiquement.  
  
5.  Générez le projet et démarrer le débogage pour tester l'affichage de la nouvelle commande.  
  
     Sur le **TestMenu** menu, cliquez sur le nouveau sous\-menu **sous\-menu**, pour afficher la nouvelle commande **espace réservé MRU**. Après avoir implémenté une liste dynamique des commandes dans la procédure suivante, cette étiquette de la commande sera remplacée par cette liste chaque fois que le sous\-menu s'ouvre.  
  
## Remplir la liste des derniers fichiers utilisés  
  
1.  Dans TestCommandPackageGuids.cs, ajoutez les lignes suivantes après l'ID de commande existantes dans le `TestCommandPackageGuids` définition de classe.  
  
    ```c#  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  Dans TestCommand.cs, ajoutez le code suivant à l'aide d'instruction.  
  
    ```c#  
    using System.Collections;  
    ```  
  
3.  Ajoutez le code suivant dans le constructeur TestCommand après le dernier appel de AddCommand. Le `InitMRUMenu` seront définis ultérieurement  
  
    ```c#  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Ajoutez le code suivant dans la classe TestCommand. Ce code initialise la liste de chaînes qui représentent les éléments à afficher dans la liste des derniers fichiers utilisés.  
  
    ```c#  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5.  Après le `InitializeMRUList` \(méthode\), ajoutez le `InitMRUMenu` \(méthode\). Ce code initialise les commandes de menu liste des derniers fichiers utilisés.  
  
    ```c#  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     Vous devez créer un objet de commande de menu pour chaque article dans la liste des derniers fichiers utilisés. Les appels IDE la `OnMRUQueryStatus` méthode pour chaque élément dans la liste des derniers fichiers utilisés jusqu'à ce qu'il y a plus d'éléments. Dans le code managé, la seule manière de l'IDE de savoir qu'il n'y a plus d'éléments est d'abord créer tous les éléments possibles. Si vous le souhaitez, vous pouvez marquer des éléments supplémentaires comme non visibles à tout d'abord à l'aide de `mc.Visible = false;` après la création de la commande de menu. Ces éléments peuvent ensuite être rendus visibles ultérieurement à l'aide de `mc.Visible = true;` dans les `OnMRUQueryStatus` \(méthode\).  
  
6.  Après le `InitMRUMenu` \(méthode\), ajoutez le code suivant `OnMRUQueryStatus` méthode. C'est le gestionnaire qui définit le texte de chaque élément des derniers fichiers utilisés.  
  
    ```c#  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  Après le `OnMRUQueryStatus` \(méthode\), ajoutez le code suivant `OnMRUExec` méthode. C'est le Gestionnaire de sélection d'un élément des derniers fichiers utilisés. Cette méthode déplace l'élément sélectionné vers le haut de la liste, puis affiche l'élément sélectionné dans une boîte de message.  
  
    ```c#  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## Test de la liste des derniers fichiers utilisés  
  
#### Pour tester la dernière liste de menu  
  
1.  Générez le projet et démarrer le débogage  
  
2.  Sur le **TestMenu** menu, cliquez sur **TestCommand appeler**. Cette opération affiche un message qui indique que la commande a été sélectionnée.  
  
    > [!NOTE]
    >  Cette étape est nécessaire pour forcer le VSPackage pour charger et afficher correctement la liste des derniers fichiers utilisés. Si vous ignorez cette étape, la liste des derniers fichiers utilisés ne s'affiche pas.  
  
3.  Sur le **Menu Test** menu, cliquez sur **sous\-menu**. Une liste de quatre éléments s'affiche à la fin du sous\-menu, sous un séparateur. Lorsque vous cliquez sur **élément 3**, une boîte de message doit apparaître et afficher le texte, « élément sélectionné 3 ». \(Si la liste des quatre éléments n'est pas affichée, vérifiez que vous avez suivi les instructions de l'étape précédente.\)  
  
4.  Ouvrez à nouveau le sous\-menu. Notez que **élément 3** est maintenant en haut de la liste et les autres éléments ont été déplacées vers le bas une position. Cliquez sur **élément 3** à nouveau et notez que la boîte de message s'affiche toujours « élément sélectionné 3 », ce qui indique que le texte a été déplacé correctement vers la nouvelle position avec l'étiquette de la commande.  
  
## Voir aussi  
 [Ajouter dynamiquement des éléments de Menu](../extensibility/dynamically-adding-menu-items.md)