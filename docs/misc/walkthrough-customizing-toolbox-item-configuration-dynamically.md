---
title: "Proc&#233;dure pas &#224; pas&#160;: personnalisation dynamique de la configuration des &#233;l&#233;ments de la bo&#238;te &#224; outils | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Boîte à outils (Kit SDK Visual Studio), ajout de contrôles (formats personnalisés)"
ms.assetid: 761f44b7-c748-4ff5-921f-fc4f71784b0e
caps.latest.revision: 45
caps.handback.revision: 45
manager: "douge"
---
# Proc&#233;dure pas &#224; pas&#160;: personnalisation dynamique de la configuration des &#233;l&#233;ments de la bo&#238;te &#224; outils
Cette procédure pas à pas montre comment un VSPackage managé peut fournir la prise en charge de la configuration dynamique des objets <xref:System.Drawing.Design.ToolboxItem>.  
  
> [!NOTE]
>  La façon la plus simple d’ajouter des contrôles personnalisés à la boîte à outils consiste à utiliser les modèles de contrôles de boîte à outils contenus dans le Kit de développement Visual Studio SDK. Cette rubrique concerne le développement de boîte à outils avancé.  
>   
>  Pour plus d’informations sur la façon de créer des contrôles de boîte à outils à l’aide des modèles, consultez [Comment : créer un contrôle de boîte à outils qui utilise Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) et [Création d’un contrôle de boîte à outils WPF](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 Cette procédure pas à pas présente les étapes suivantes :  
  
1.  Ajouter et inscrire correctement tous les contrôles **Toolbox** dans les objets VSPackage à l’aide des classes <xref:System.ComponentModel.ToolboxItemAttribute> et <xref:System.Drawing.ToolboxBitmapAttribute>.  
  
2.  Créer les deux contrôles suivants et ajouter des icônes pour chacun d’eux à la **Toolbox** :  
  
    -   Un contrôle qui déclare un <xref:System.Drawing.Design.ToolboxItem> par défaut associé  
  
    -   Un contrôle qui déclare un élément **Toolbox** personnalisé associé qui dérive de la classe <xref:System.Drawing.Design.ToolboxItem>  
  
3.  Écrire une implémentation de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> et l’inscrire en procédant comme suit :  
  
    1.  Définir une classe de filtre qui dérive de la classe <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> et spécifie les instances <xref:System.Drawing.Design.ToolboxItem> sur lesquelles cette implémentation agira  
  
    2.  Appliquer un <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute>, qui fait référence à la classe de filtre, à la classe qui implémente la classe <xref:Microsoft.VisualStudio.Shell.Package> pour le VSPackage  
  
4.  Inscrire le VSPackage en tant que fournisseur d’objets <xref:System.Drawing.Design.ToolboxItem> en appliquant le <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> à la classe qui implémente la classe <xref:Microsoft.VisualStudio.Shell.Package> pour le VSPackage.  
  
5.  Au moment du chargement du package, utiliser la réflexion pour générer une liste de tous les objets <xref:System.Drawing.Design.ToolboxItem> fournis par le VSPackage.  
  
6.  Créer un gestionnaire pour les événements <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> et <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>. Cela garantit que les objets <xref:System.Drawing.Design.ToolboxItem> du VSPackage sont chargés correctement.  
  
7.  Implémenter une commande sur le VSPackage pour forcer la réinitialisation de la **Toolbox**.  
  
## Composants requis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement Visual Studio SDK. Pour plus d'informations, consultez [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Emplacements du modèle de projet de package Visual Studio  
 Le modèle de projet de package Visual Studio se trouve à trois emplacements différents dans la boîte de dialogue **Nouveau projet** :  
  
1.  Sous Extensibilité Visual Basic. Le langage par défaut du projet est Visual Basic.  
  
2.  Sous Extensibilité C\#. Le langage par défaut du projet est C\#.  
  
3.  Sous Extensibilité d’autres types de projets. Le langage par défaut du projet est C\#.  
  
## Création d’un VSPackage managé  
 Appliquez les procédures suivantes pour créer un VSPackage managé.  
  
#### Pour créer un VSPackage managé pour fournir des éléments de boîte à outils  
  
1.  Créez un VSPackage nommé `ItemConfiguration`. Pour plus d'informations, consultez [Procédure pas à pas : création d’une commande de menu à l’aide du modèle de package Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  Dans le modèle **Package Visual Studio**, ajoutez une commande de menu.  
  
     Nommez la commande `Initialize ItemConfigurationVB` pour Visual Basic ou `Initialize ItemConfigurationCS` pour Visual C\#.  
  
3.  Pour [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], ajoutez les espaces de noms suivants à la liste d’espaces de noms importés dans le projet généré :  
  
    -   Company.ItemConfiguration  
  
    -   Système  
  
    -   System.ComponentModel  
  
    -   System.Drawing  
  
    -   System.Windows.Forms  
  
4.  Ajoutez une référence au composant .NET Framework <xref:System.Drawing.Design?displayProperty=fullName>.  
  
 Si vous appliquez cette procédure pas à pas pour plusieurs langages, vous devez mettre à jour le projet pour supprimer l’ambiguïté entre les assemblys générés.  
  
#### Pour supprimer l’ambiguïté entre les VSPackages Visual Basic et Visual C\#  
  
1.  Pour [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] :  
  
    1.  Ouvrez les propriétés du projet, puis sélectionnez l’onglet **Application**.  
  
         Remplacez le nom de l’assembly par `ItemConfigurationVB` et remplacez l’espace de noms par défaut par `Company.ItemConfigurationVB`.  
  
    2.  Sélectionnez l’onglet **Références**.  
  
         Mettez à jour la liste des espaces de noms importés.  
  
         Supprimez Company.ItemConfiguration.  
  
         Ajoutez Company.ItemConfigurationVB.  
  
2.  Pour [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] :  
  
    1.  Ouvrez les propriétés du projet, puis sélectionnez l’onglet **Application**.  
  
         Remplacez le nom de l’assembly par `ItemConfigurationCS` et remplacez l’espace de noms par défaut par `Company.ItemConfigurationCS`.  
  
    2.  Ouvrez la classe ItemConfigurationPackage dans l’éditeur de code.  
  
         Pour utiliser les outils de refactorisation pour renommer l’espace de noms existant, cliquez sur le nom de l’espace de noms existant, `ItemConfiguration`, pointez sur **Refactoriser**, puis cliquez sur **Renommer**. Remplacez le nom par `ItemConfigurationCS`.  
  
3.  Enregistrez toutes les modifications.  
  
#### Pour tester le code généré  
  
1.  Compilez et démarrez le VSPackage dans la ruche expérimentale de Visual Studio.  
  
2.  Dans le menu **Outils**, cliquez sur **Initialiser Item Configuration VB** ou **Initialiser Item Configuration CS**.  
  
     Cette opération ouvre une boîte de message qui contient du texte signalant que le gestionnaire d’élément de menu du package a été appelé.  
  
3.  Fermez la version expérimentale de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
## Création de contrôles de boîte à outils  
 Dans cette section, vous allez créer et inscrire un contrôle utilisateur, `Control1`, qui déclare un élément **Toolbox** par défaut associé. Vous allez également créer et inscrire un deuxième contrôle utilisateur, `Control2`, et un élément **Toolbox** personnalisé associé, `Control2_ToolboxItem`, qui dérive de la classe <xref:System.Drawing.Design.ToolboxItem>. Pour plus d’informations sur la façon de créer des contrôles Windows Forms et des classes <xref:System.Drawing.Design.ToolboxItem>, consultez [Développement de contrôles Windows Forms au moment du design](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
#### Pour créer des éléments de boîte à outils personnalisés et par défaut  
  
1.  Suivez les instructions de [Procédure pas à pas : chargement automatique d’éléments de boîte à outils](../Topic/Walkthrough:%20Autoloading%20Toolbox%20Items.md) pour créer un élément **Toolbox** par défaut et un élément **Toolbox** personnalisé comme suit.  
  
    1.  Terminez la procédure intitulée « Pour créer un contrôle **Toolbox** qui sera utilisé avec un ToolboxItem par défaut ». Mettez à jour le <xref:System.ComponentModel.DescriptionAttribute> pour qu’il fasse référence à ce projet.  
  
         Le code résultant de la classe `Control1` doit ressembler au code suivant.  
  
         [!code-cs[DynamicToolboxMembers#01](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_1.cs)]
         [!code-vb[DynamicToolboxMembers#01](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_1.vb)]  
  
    2.  Terminez la procédure intitulée « Pour créer un contrôle **Toolbox** pour l’utilisation d’une classe personnalisée dérivée de ToolboxItem ». Mettez à jour le <xref:System.ComponentModel.DescriptionAttribute> pour qu’il fasse référence à ce projet.  
  
         Le code résultant des classes `Control2` et `Control2_ToolboxItem` doit ressembler au code suivant.  
  
         [!code-vb[DynamicToolboxMembers#02](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_2.vb)]
         [!code-cs[DynamicToolboxMembers#02](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_2.cs)]  
  
2.  Enregistrez les fichiers.  
  
## Incorporation d’icônes de bitmaps  
 L’attribut <xref:System.Drawing.ToolboxBitmapAttribute> appliqué à chaque contrôle spécifie l’icône à associer à ce contrôle. Créez les bitmaps pour les deux contrôles et nommez\-les comme suit :  
  
-   `Control1.bmp` pour la classe `Control1`.  
  
-   `Control2.bmp` pour la classe `Control2`.  
  
#### Pour incorporer une icône bitmap pour un élément Toolbox  
  
1.  Ajoutez une nouvelle bitmap au projet, comme suit :  
  
    1.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet VSPackage, pointez sur **Ajouter**, puis cliquez sur **Nouvel élément**.  
  
    2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Fichier bitmap**, puis entrez le nom de la bitmap.  
  
2.  Utilisez l’éditeur de bitmaps pour créer une icône de 16x16, comme suit.  
  
    1.  Dans le menu **Affichage**, cliquez sur **Fenêtre Propriétés**.  
  
    2.  Dans la fenêtre **Propriétés**, affectez la valeur 16 à **Hauteur** et **Largeur**.  
  
    3.  Utilisez l’éditeur pour créer l’image d’icône.  
  
3.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur l’élément de bitmap, puis cliquez sur **Propriétés**.  
  
4.  Affectez la valeur **Ressource incorporée** à la propriété **Action de génération**.  
  
5.  Enregistrez tous les fichiers ouverts.  
  
## Ajout d’un fournisseur de configuration de boîte à outils dynamique  
 Dans cette section, vous allez créer et inscrire une classe qui implémente l’interface <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>. Cette classe est instanciée et utilisée par l’environnement de développement intégré \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour configurer des contrôles **Toolbox**.  
  
> [!NOTE]
>  Étant donné que l’environnement [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instancie une instance de l’implémentation de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>, vous ne devez pas implémenter l’interface <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> sur la classe qui implémente <xref:Microsoft.VisualStudio.Shell.Package> pour un VSPackage.  
  
#### Pour créer et inscrire un objet de configuration de contrôle de boîte à outils  
  
1.  Dans **l’Explorateur de solutions**, ajoutez une classe au projet ItemConfiguration et nommez\-la `ToolboxConfig`.  
  
2.  Ajoutez les instructions d’espace de noms suivantes au fichier.  
  
     [!code-cs[DynamicToolboxMembers#03](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_3.cs)]
     [!code-vb[DynamicToolboxMembers#03](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_3.vb)]  
  
3.  Vérifiez que la classe `ToolboxConfig` est `public` et implémente l’interface <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>.  
  
4.  Appliquez un <xref:System.Runtime.InteropServices.GuidAttribute> et un <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> à la classe `ToolboxConfig``.`  
  
    -   Pour [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], utilisez `"ItemConfigurationVB, Version=*, Culture=*, PublicKeyToken=*"` comme nom d’assembly.  
  
    -   Pour [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], utilisez `"ItemConfigurationCS, Version=*, Culture=*, PublicKeyToken=*"` comme nom d’assembly.  
  
     Cela limite la classe `ToolboxConfig` à l’utilisation des objets <xref:System.Drawing.Design.ToolboxItem> qui sont fournis par l’assembly qui contient le VSPackage actuel.  
  
     [!code-cs[DynamicToolboxMembers#04](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_4.cs)]
     [!code-vb[DynamicToolboxMembers#04](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_4.vb)]  
  
     Vous pouvez générer un GUID en cliquant sur **Créer un GUID** dans le menu **Outils**. Sélectionnez **le format avec crochets**, cliquez sur **Copier**, puis collez le GUID dans votre code. Remplacez le mot clé `GUID` par `Guid`.  
  
5.  Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> de l’interface <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> pour qu’elle agisse uniquement sur les deux classes <xref:System.Drawing.Design.ToolboxItem>, `Control1` et `Control2`.  
  
     L’implémentation de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> applique des instances de <xref:System.ComponentModel.ToolboxItemFilterAttribute> aux deux objets <xref:System.Drawing.Design.ToolboxItem> pour que :  
  
    -   Le <xref:System.Drawing.Design.ToolboxItem> qui est implémenté par `Control1` est accessible uniquement dans la **Toolbox** aux concepteurs qui gèrent des objets <xref:System.Windows.Forms.UserControl>  
  
    -   Le <xref:System.Drawing.Design.ToolboxItem> qui est implémenté par `Control2` n’est pas accessible dans la **Toolbox** aux concepteurs qui gèrent des objets <xref:System.Windows.Forms.UserControl>  
  
     [!code-cs[DynamicToolboxMembers#05](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_5.cs)]
     [!code-vb[DynamicToolboxMembers#05](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_5.vb)]  
  
## Modification de l’implémentation du VSPackage  
 Vous devez modifier l’implémentation par défaut du package VS fournie par le modèle de package [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour qu’elle effectue les opérations suivantes :  
  
-   S’inscrire en tant que fournisseur d’élément **Toolbox**  
  
-   Inscrire la classe qui fournit la configuration dynamique des contrôles **Toolbox** pour le VSPackage  
  
-   Utiliser le <xref:System.Drawing.Design.ToolboxService> pour charger tous les objets <xref:System.Drawing.Design.ToolboxItem> fournis par l’assembly VSPackage  
  
-   Gérer les événements <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> et <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>  
  
#### Pour modifier l’implémentation de package pour un fournisseur d’éléments Toolbox sur le VSPackage  
  
1.  Ouvrez la classe ItemConfigurationPackage dans l’éditeur de code.  
  
2.  Modifiez la déclaration de la classe `ItemConfigurationPackage`, qui est l’implémentation de la classe <xref:Microsoft.VisualStudio.Shell.Package> dans la solution.  
  
    1.  Ajoutez les instructions d’espace de noms suivantes au fichier.  
  
         [!code-vb[DynamicToolboxMembers#06](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_6.vb)]
         [!code-cs[DynamicToolboxMembers#06](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_6.cs)]  
  
    2.  Pour inscrire le VSPackage comme fournissant des éléments **Toolbox**, appliquez un <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> au package. Pour inscrire la classe `ToolboxConfig` comme fournissant une configuration dynamique des contrôles **Toolbox**, appliquez un <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> au package.  
  
         [!code-vb[DynamicToolboxMembers#07](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_7.vb)]
         [!code-cs[DynamicToolboxMembers#07](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_7.cs)]  
  
        > [!NOTE]
        >  Le seul argument de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> est la version de <xref:System.Drawing.Design.ToolboxItem> fournie par le VSPackage. En modifiant cette valeur, vous forcez l’IDE à charger le VSPackage même s’il possède une version précédemment mise en cache de <xref:System.Drawing.Design.ToolboxItem>.  
  
    3.  Créez deux champs `private` dans la classe `ItemConfiguration`, comme suit :  
  
         Un membre <xref:System.Collections.ArrayList>, nommé `ToolboxItemList`, pour conserver une liste des objets <xref:System.Drawing.Design.ToolboxItem> gérés par la classe `ItemConfiguration`.  
  
         Un <xref:System.String>, nommé `CategoryTab`, qui contient l’onglet **Toolbox** qui sert à conserver les objets <xref:System.Drawing.Design.ToolboxItem> gérés par la classe `ItemConfiguration`.  
  
         [!code-vb[DynamicToolboxMembers#08](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_8.vb)]
         [!code-cs[DynamicToolboxMembers#08](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_8.cs)]  
  
     Le résultat de cette modification ressemble au code suivant :  
  
     [!code-vb[DynamicToolboxMembers#09](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_9.vb)]
     [!code-cs[DynamicToolboxMembers#09](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_9.cs)]  
  
3.  Définissez une méthode `OnRefreshToolbox` pour gérer les événements <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> et <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>.  
  
     La méthode `OnRefreshToolbox` utilise la liste d’objets <xref:System.Drawing.Design.ToolboxItem> contenue dans le champ `ToolboxItemList` et exécute les actions suivantes :  
  
    -   Elle supprime tous les objets <xref:System.Drawing.Design.ToolboxItem> de l’onglet **Toolbox** défini par le champ `CategoryTab`.  
  
    -   Elle ajoute à l’onglet **Toolbox** de nouvelles instances de tous les objets <xref:System.Drawing.Design.ToolboxItem> qui sont répertoriés dans le champ `ToolboxItemList`.  
  
    -   Elle définit l’onglet **Toolbox** comme onglet actif.  
  
     [!code-vb[DynamicToolboxMembers#10](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_10.vb)]
     [!code-cs[DynamicToolboxMembers#10](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_10.cs)]  
  
4.  Pour [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], dans le constructeur, inscrivez la méthode `OnRefreshToolbox` comme gestionnaire d’événements pour les événements <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> et <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>.  
  
     [!code-cs[DynamicToolboxMembers#11](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_11.cs)]  
  
5.  Modifiez la méthode `Initialize` dans `ItemConfigurationPackage` pour remplir le champ `ToolboxItemList` en appelant la méthode <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A> de la classe <xref:System.Drawing.Design.ToolboxService?displayProperty=fullName>. Le service **Toolbox** obtient toutes les classes d’éléments **Toolbox** qui sont définies dans l’assembly en cours d’exécution. Le champ `ToolboxItemList` est utilisé par les gestionnaires d’événements **Toolbox** pour charger les éléments **Toolbox**.  
  
     Ajoutez le code suivant à la fin de la méthode `Initialize`.  
  
     [!code-vb[DynamicToolboxMembers#12](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_12.vb)]
     [!code-cs[DynamicToolboxMembers#12](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_12.cs)]  
  
    > [!NOTE]
    >  En guise d’exercice, vous pourriez développer un mécanisme pour tester la version du VSPackage ou des éléments, et effectuer une mise à jour uniquement si la version du VSPackage ou du <xref:System.Drawing.Design.ToolboxItem> a changé.  
  
## Initialisation de la Toolbox  
  
#### Pour implémenter une commande pour initialiser la Toolbox  
  
-   Dans la classe `ItemConfigurationPackage`, modifiez la méthode `MenuItemCallBack`, qui est le gestionnaire de commandes de l’élément de menu.  
  
     Remplacez l’implémentation existante de la méthode `MenuItemCallBack` en exécutant le code suivant :  
  
     [!code-vb[DynamicToolboxMembers#13](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_13.vb)]
     [!code-cs[DynamicToolboxMembers#13](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_13.cs)]  
  
## Génération et exécution de la solution  
 Vous pouvez tester le produit de cette procédure pas à pas à l’aide d’une instance de Visual Studio qui s’exécute dans la ruche expérimentale.  
  
#### Pour tester cette procédure pas à pas  
  
1.  Dans Visual Studio, dans le menu **Générer**, cliquez sur **Régénérer la solution**.  
  
2.  Appuyez sur F5 pour démarrer une seconde instance de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans la ruche du Registre expérimentale.  
  
     Pour plus d’informations sur la façon d’utiliser la ruche du Registre expérimentale, consultez [L'Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
3.  Cliquez sur le menu **Outils**.  
  
     Une commande nommée **Initialiser ItemConfiguration VB** ou **Initialiser ItemConfiguration CS** apparaît en haut du menu, avec une icône qui a la valeur 1.  
  
4.  Créez une application Windows Forms [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
     Un concepteur basé sur des formulaires \(<xref:System.Windows.Forms.Form>\) s’affiche.  
  
5.  Ajoutez un contrôle utilisateur au projet  
  
     Un concepteur de contrôles utilisateur s’affiche.  
  
6.  Épinglez la **Toolbox** en position ouverte et basculez entre les deux vues de conception.  
  
     Notez que l’élément **Toolbox** visible dépend du concepteur qui a le focus.  
  
7.  Faites glisser le premier élément **Toolbox** sur le contrôle utilisateur pour ajouter une instance de `Control1` au contrôle utilisateur.  
  
8.  Faites glisser le second élément **Toolbox** sur le formulaire pour ajouter une instance de `Control2` au formulaire.  
  
9. Générez l’application Windows.  
  
     Le contrôle utilisateur pour l’application est maintenant disponible dans la **Toolbox**.  
  
10. Ajoutez le contrôle utilisateur de l’application au formulaire, puis régénérez l’application et exécutez\-la.  
  
     Lorsque l’application s’exécute, cliquez sur chaque contrôle sur le formulaire pour afficher la boîte de message associée.  
  
## Analyse de l’implémentation  
 Le paramètre `assemblyFilter` étant présent dans le constructeur de classe <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute>, seuls les objets <xref:System.Drawing.Design.ToolboxItem> dans l’assembly généré lors de cette procédure pas à pas sont traités par la méthode <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> de la classe `ToolboxConfg`.  
  
 Ainsi, chaque fois que la catégorie **ItemConfiguration Walkthrough** est active sur la **Toolbox**, la méthode <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> de la classe `ToolboxConfg` est appelée et les instances de <xref:System.ComponentModel.ToolboxItemFilterAttribute> sont appliquées aux objets <xref:System.Drawing.Design.ToolboxItem> implémentés par `Control1` et `Control2`.  
  
## Voir aussi  
 [Extension de la boîte à outils](../misc/extending-the-toolbox.md)   
 [Inscription des fonctionnalités de prise en charge de boîte à outils](../misc/registering-toolbox-support-features.md)   
 [Développement avancé de contrôles de boîte à outils](/visual-cpp/misc/advanced-toolbox-control-development)   
 [Procédures pas à pas de la Boîte à outils](../misc/toolbox-walkthroughs.md)