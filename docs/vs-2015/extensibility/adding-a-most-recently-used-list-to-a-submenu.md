---
title: Ajout d’une liste à un sous-menu utilisés récemment | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 47
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 327d312ec13e449f0e116a11f920f17a439f569c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818099"
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>Ajout d’une liste de fichiers récents à un sous-menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas s’appuie sur des démonstrations de [Ajout d’un sous-menu à un Menu](../extensibility/adding-a-submenu-to-a-menu.md)et montre comment ajouter une liste dynamique à un sous-menu. La liste dynamique constitue la base pour la création d’une liste plus récemment utilisés (MRU).  
  
 Une liste de menu dynamique commence par un espace réservé dans un menu. Chaque fois que le menu est affiché, l’environnement de développement intégré (IDE) Visual Studio vous demande le VSPackage pour toutes les commandes qui doivent être affichées à l’espace réservé. Une liste dynamique peut se produire à n’importe où dans un menu. Toutefois, les listes dynamiques sont généralement stockés et affichés par eux-mêmes de sous-menus ou au bas de menus. À l’aide de ces modèles de conception, vous activez la liste dynamique des commandes pour développer et réduire sans affecter la position des autres commandes dans le menu. Dans cette procédure pas à pas, la liste des fichiers récents dynamique s’affiche en bas d’un sous-menu existant, séparé du reste du sous-menu par une ligne.  
  
 Techniquement, une liste dynamique peut également être appliquée à une barre d’outils. Toutefois, nous déconseillons cette utilisation, car une barre d’outils doit rester inchangé, sauf si l’utilisateur effectue les étapes spécifiques pour le modifier.  
  
 Cette procédure pas à pas crée une liste des fichiers récents des quatre éléments qui modifient leur ordre chaque fois qu’un d'entre eux est sélectionné (l’élément sélectionné se déplace vers le haut de la liste).  
  
 Pour plus d’informations sur les menus et les fichiers .vsct, consultez [commandes, Menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-an-extension"></a>Création d’une Extension  
  
- Suivez les procédures de [Ajout d’un sous-menu à un Menu](../extensibility/adding-a-submenu-to-a-menu.md) pour créer le sous-menu est modifié dans les procédures suivantes.  
  
  Les procédures décrites dans cette procédure pas à pas supposent que le nom du VSPackage est `TopLevelMenu`, qui est le nom qui est utilisé dans [Ajout d’un Menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## <a name="creating-a-dynamic-item-list-command"></a>Création d’une commande de la liste élément dynamique  
  
1.  Ouvrez TestCommandPackage.vsct.  
  
2.  Dans le `Symbols` section, dans le `GuidSymbol` nœud nommé guidTestCommandPackageCmdSet, ajoutez le symbole pour le `MRUListGroup` groupe et le `cmdidMRUList` de commande, comme suit.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  Dans la `Groups` section, ajoutez le groupe déclaré après les entrées de groupe existant.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  Dans le `Buttons` , ajoutez un nœud pour représenter la commande qui vient d’être déclarée, après les entrées existantes de bouton.  
  
    ```csharp  
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
  
     Le `DynamicItemStart` indicateur Active la commande comme étant générée dynamiquement.  
  
5.  Générez le projet et démarrer le débogage pour tester l’affichage de la nouvelle commande.  
  
     Sur le **TestMenu** menu, cliquez sur le nouveau sous-menu **sous-menu**, pour afficher la nouvelle commande **espace réservé MRU**. Une fois une liste des fichiers récents dynamique des commandes est implémentée dans la procédure suivante, cette étiquette de la commande sera remplacée par cette liste chaque fois que le sous-menu est ouvert.  
  
## <a name="filling-the-mru-list"></a>Remplissage de la liste des fichiers récents  
  
1.  Dans TestCommandPackageGuids.cs, ajoutez les lignes suivantes après l’ID de commande existants dans le `TestCommandPackageGuids` définition de classe.  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  Dans TestCommand.cs, ajoutez le code suivant à l’aide d’instruction.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3.  Ajoutez le code suivant dans le constructeur de la commande de test après le dernier appel de AddCommand. Le `InitMRUMenu` seront définis ultérieurement  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Ajoutez le code suivant dans la classe de commande de test. Ce code initialise la liste de chaînes qui représentent les éléments à afficher dans la liste des derniers fichiers utilisés.  
  
    ```csharp  
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
  
5.  Après le `InitializeMRUList` (méthode), ajoutez le `InitMRUMenu` (méthode). Ce code initialise les commandes de menu de liste des derniers fichiers utilisés.  
  
    ```csharp  
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
  
     Vous devez créer un objet de commande de menu pour chaque élément possible dans la liste des derniers fichiers utilisés. Les appels de l’IDE le `OnMRUQueryStatus` méthode pour chaque élément dans la liste des derniers fichiers utilisés jusqu'à ce qu’il n’y a aucuns autres éléments. Dans le code managé, la seule façon de l’IDE de savoir qu’il n’y a aucun élément supplémentaire est d’abord créer tous les éléments possibles. Si vous le souhaitez, vous pouvez marquer des éléments supplémentaires comme n’étant pas visible à tout d’abord à l’aide de `mc.Visible = false;` après la création de la commande de menu. Ces éléments peuvent ensuite être rendus visibles ultérieurement à l’aide de `mc.Visible = true;` dans le `OnMRUQueryStatus` (méthode).  
  
6.  Après le `InitMRUMenu` (méthode), ajoutez le code suivant `OnMRUQueryStatus` (méthode). Il s’agit de gestionnaire qui définit le texte pour chaque élément de la liste des fichiers récents.  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  Après le `OnMRUQueryStatus` (méthode), ajoutez le code suivant `OnMRUExec` (méthode). Ceci est le gestionnaire pour la sélection d’un élément de la liste des fichiers récents. Cette méthode déplace l’élément sélectionné vers le haut de la liste, puis affiche l’élément sélectionné dans une boîte de message.  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
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
  
## <a name="testing-the-mru-list"></a>Test de la liste des fichiers récents  
  
#### <a name="to-test-the-mru-menu-list"></a>Pour tester la dernière liste de menu  
  
1.  Générer le projet et démarrer le débogage  
  
2.  Sur le **TestMenu** menu, cliquez sur **appeler la commande de test**. Cette opération affiche un message qui indique que la commande a été sélectionnée.  
  
    > [!NOTE]
    >  Cette étape est nécessaire pour forcer le VSPackage pour charger et afficher correctement la liste des derniers fichiers utilisés. Si vous ignorez cette étape, la liste des derniers fichiers utilisés n’est pas affichée.  
  
3.  Sur le **Menu Test** menu, cliquez sur **sous-menu**. Une liste d’éléments de quatre s’affiche à la fin du sous-menu ci-dessous un séparateur. Lorsque vous cliquez sur **élément 3**, une boîte de message doit apparaître et afficher le texte, « Selected Item 3 ». (Si la liste des quatre éléments n’est pas affichée, vérifiez que vous avez suivi les instructions de l’étape précédente.)  
  
4.  Ouvrez le sous-menu à nouveau. Notez que **élément 3** est maintenant en haut de la liste et les autres éléments ont été déplacées vers le bas une position. Cliquez sur **élément 3** à nouveau et notez que la boîte de message affiche toujours « Selected Item 3 », ce qui indique que le texte a été déplacé correctement vers la nouvelle position avec l’étiquette de la commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout dynamique d’éléments de menu](../extensibility/dynamically-adding-menu-items.md)

