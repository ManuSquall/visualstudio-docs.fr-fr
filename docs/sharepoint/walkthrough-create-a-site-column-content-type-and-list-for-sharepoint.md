---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;une colonne de site, d&#39;un type de contenu et d&#39;une liste pour SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.ListDesigner.GeneralMessageHelp"
  - "Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping"
  - "VS.SharePointTools.ListDesigner.SortingGrouping"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, types de contenu"
  - "développement SharePoint dans Visual Studio, champs"
  - "développement SharePoint dans Visual Studio, définitions de listes"
  - "développement SharePoint dans Visual Studio, instances de listes"
ms.assetid: caebacc2-616c-4373-8e21-edc7979338e7
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;une colonne de site, d&#39;un type de contenu et d&#39;une liste pour SharePoint
  Les procédures suivantes montrent comment créer des colonnes de site SharePoint personnalisées—ou *champ*— de la même manière qu'un type de contenu utilisant les colonnes de site.  Il montre également comment créer une liste qui utilise le nouveau type de contenu.  
  
 Cette procédure pas à pas comprend les tâches suivantes :  
  
-   [Créer des colonnes personnalisées de site](#BKMK_CreatingCustSiteCols).  
  
-   [Création d'un type de contenu personnalisé](#BKMK_CreateCustContType).  
  
-   [Créer une liste](#BKMK_CreateList).  
  
-   [Créer une liste](#BKMK_CreateList).  
  
-   [Test de l'application](#BKMK_TestApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Windows et SharePoint.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
##  <a name="BKMK_CreatingCustSiteCols"></a> Créer des colonnes personnalisées de site  
 Cet exemple crée une liste de gestion des patients dans un hôpital.  D'abord, vous devez créer un projet dans SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et lui ajouter des colonnes de site, comme suit.  
  
#### Pour créer le projet  
  
1.  Dans le menu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Fichier**, cliquez sur **Nouveau**, **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sous **Visual Basic** ou **Visual C\#**, développez le noeud **SharePoint**, puis cliquez sur **2010**.  
  
3.  Dans le volet **Modèles**, cliquez sur **Projet SharePoint 2010** , remplacez le nom du projet par Clinic, puis cliquez sur **OK**.  
  
     Le modèle de projet SharePoint 2010 est un projet vide utilisé dans cet exemple pour contenir des colonnes de site et autres éléments de projet qui sont ajoutées ultérieurement.  
  
4.  Dans la page **Spécifier le site et le niveau de sécurité pour le débogage**, entrez l'URL du site local SharePoint auquel vous souhaitez ajouter le nouvel élément de champ personnalisé ou utilisez l'emplacement par défaut \(`http://<`*SystemName*`>/)`.\).  
  
5.  Dans la section **Quel est le niveau de confiance de cette solution SharePoint ?**, utilisez la valeur par défaut de **Déployer en tant que solution bac à sable \(sandbox\)**.  
  
     Pour plus d'informations sur les solutions bac à sable \(sandbox\) et les solutions de batterie, consultez [Considérations sur les solutions bac à sable &#40;sandbox&#41;](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Choisissez le bouton **Terminer**.  Le projet doit maintenant apparaître dans **Explorateur de solutions**.  
  
#### Pour ajouter des colonnes de site  
  
1.  Ajoutez une colonne de sites.  Pour cela, dans l'**Explorateur de solutions**, ouvrez le menu contextuel de **Clinic**, puis choisissez **Ajouter**, **Nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez le champ **Colonne de site**, remplacez le nom par Patient Name puis choisissez le bouton **Ajouter**.  
  
3.  Dans le fichier à Elements.xml de la colonne de site, laissez le paramètre **Type** définit comme **Texte**, puis remplacez le paramètre **Groupe** par Colonnes de site Clinic.  Lorsque vous avez terminé, le fichier Elements.xml de la colonne du site doit ressembler à l'exemple suivant.  
  
    ```  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  À l'aide de la procédure, ajoutez deux ou plusieurs colonnes de site au projet : Patient ID \(Type \= "Integer"\) and Doctor Name \(Type \= "Text"\).  Définissez la valeur de groupe de colonnes du site Clinic.  
  
##  <a name="BKMK_CreateCustContType"></a> Création d'un type de contenu personnalisé  
 Ensuite, créez un type de contenu basé sur le type de contenu Contacts qui contient les colonnes du site que vous avez créées dans la procédure précédente.  En basant un type de contenu sur un type de contenu existant, vous pouvez gagner du temps car le type de contenu de base fournit plusieurs colonnes de site à utiliser dans le nouveau type de contenu.  
  
#### Pour créer un type de contenu personnalisé  
  
1.  Ajoutez un type de contenu au projet.  Pour cela, dans l'**Explorateur de solutions**, choisissez le nœud du projet.  
  
2.  Dans la barre de menus, choisissez **Projet**, **Ajouter un nouvel élément**.  
  
3.  Sous **Visual C\#** ou **Visual Basic**, développez le nœud **SharePoint**, puis cliquez sur le noeud **2010**.  
  
4.  Dans le volet **Modèles**, sélectionnez le modèle **Type de contenu**, remplacez le nom par Patient Info, puis cliquez sur le bouton **Ajouter**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
5.  Dans la liste **De quel type de contenu de base ce type de contenu devrait hérité**, choisissez **Contact** comme type de contenu sur lequel le nouveau type de contenu doit être basé, puis choisir le bouton **Terminer**.  
  
     Cette opération permet l'accès à d'autres colonnes de site utile dans type de contenu de contact, en plus des colonnes de site que vous avez défini précédemment.  
  
6.  Une fois que le concepteur des types de contenu s'affiche, dans l'onglet **Colonnes**, ajoutez les trois colonnes de site que vous avez défini précédemment : **Patient Name**, **Patient ID**, et **Doctor Name**.  Pour ajouter les colonnes, choisissez la première zone de liste de la liste des colonnes de site sous **Display Name**, puis cliquez sur chaque colonne du site de la liste un par un.  
  
    > [!TIP]  
    >  Pour choisir les colonnes de site plus rapidement, filtrez la liste en entrant les premières lettres du nom de la colonne.  
  
7.  En plus des trois colonnes de site personnalisées, ajoutez la colonne du site **Commentaires** de la liste des colonnes de site.  
  
8.  Activez la case à cocher **Requis** pour des colonnes de site **Patient Name** et **Patient ID** pour y apporter des champs obligatoires.  
  
9. Sous l'onglet **Type de contenu**, vérifiez que le nom du type de contenu est **Patient Info**, puis modifiez la description pour la fiche Patient Information.  
  
10. Modifiez **Nom de groupe** aux types de contenu Clinic, et laissez les autres paramètres à leurs valeurs par défaut.  
  
11. Dans la barre de menus, cliquez sur **Fichier**, **Enregistrer tout**, puis fermez le concepteur des types de contenu.  
  
##  <a name="BKMK_CreateList"></a> Créer une liste  
 Maintenant, créez une liste qui utilise les nouvelles colonnes des types de contenu et de site.  
  
#### Pour créer une liste  
  
1.  Ajoutez une liste au projet.  Pour cela, dans l'**Explorateur de solutions**, choisissez le nœud du projet.  
  
2.  Dans la barre de menus, choisissez **Projet**, **Ajouter un nouvel élément**.  
  
3.  Sous **Visual C\#** ou **Visual Basic**, développez le nœud **SharePoint**, puis cliquez sur le noeud **2010**.  
  
4.  Dans le volet **Modèles**, sélectionnez le modèle **Liste**, remplacez le nom par Patients, puis cliquez sur le bouton **Ajouter**.  
  
5.  Laissez **Personnaliser la liste sur** défini comme **Défaut \(Vide\)**, puis cliquez sur le bouton **Terminer**.  
  
6.  Dans le concepteur de liste, sélectionnez le bouton **Types de contenu** pour afficher la boîte de dialogue **Paramètres de type de contenu**.  
  
7.  Choisissez la nouvelle ligne, choisissez le type de contenu **Patient Info** dans la liste des types de contenu, puis cliquez sur le bouton **OK**.  
  
     Cette opération ajoute toutes les colonnes de site à partir du type de contenu **Patient Info** de la liste.  
  
8.  Supprimez toutes les colonnes du site dans la liste sauf ce qui suit :  
  
    -   Patient ID  
  
    -   Patient Name  
  
    -   Home Phone  
  
    -   E\-Mail  
  
    -   Doctor Name  
  
    -   Commentaires  
  
9. Sous **Nom de la colonne**, choisissez une ligne vide, ajoutez une colonne spéciale de liste, et nommez\-la Hopital.  Laissez le type de données comme **Une seule ligne de texte**.  
  
     La colonne de la liste s'applique uniquement à cette liste.  Lorsque vous ajoutez une colonne spéciale de liste vers une liste, un nouveau type de contenu de liste, notamment les colonnes ajoutées dans la liste, est créé et configuré en tant que la liste par défaut.  
  
    > [!TIP]  
    >  Si vous choisissez une colonne dans la liste des colonnes de site, une colonne existante du site est utilisée.  Toutefois, si vous entrez une valeur de colonne sans choisir une colonne dans la liste, une colonne de la liste personnalisée est créée, même si une colonne du même nom existe déjà dans la liste.  
  
     Éventuellement, plutôt que définir le type de données pour la colonne de la liste personnalisée à **Une seule ligne de texte**, vous pouvez à la place définir le type de données de cette colonne pour rechercher, et les valeurs sont récupérées d'une table ou d'une autre liste.  Pour plus d'informations sur les colonnes de recherche, consultez [Liste de relations dans SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) et [Relations et recherches de liste](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. A côté des zones **Patient ID** et de **Patient Name**, activez la case à cocher **Requis**.  
  
11. Sous l'onglet **Vues**, choisissez une ligne vide pour créer une vue.  Entrez les informations du patient.  
  
     Sous l'onglet **Vues**, vous pouvez spécifier les colonnes que vous souhaitez afficher dans la liste SharePoint.  
  
12. Sélectionnez la ligne **Informations du patient**, puis cliquez sur le bouton **Par défaut**.  
  
     La vue est maintenant la vue par défaut pour la liste.  
  
13. Ajoutez les colonnes suivantes à la liste **Colonnes sélectionnées** dans l'ordre suivant :  
  
    -   Patient ID  
  
    -   Patient Name  
  
    -   Home Phone  
  
    -   E\-Mail  
  
    -   Doctor Name  
  
    -   Hôpital  
  
    -   Commentaires  
  
14. Dans la liste **Propriétés**, choisissez la propriété **Tri et regroupement**, puis sélectionnez le bouton ![Icône du bouton de sélection (...)](../sharepoint/media/ellipsisicon.png "Icône du bouton de sélection (...)") pour afficher la boîte de dialogue **Tri et regroupement**.  
  
15. Dans la liste **Nom de la colonne**, choisissez **Nom du patient**, assurez\-vous que la colonne **Tri** est définie sur **Croissant**, puis cliquez sur le bouton **OK**.  
  
##  <a name="BKMK_TestApp"></a> Test de l'application  
 Maintenant que les colonnes, le type de contenu, ainsi que la liste personnalisé de site sont prêts, déployez\-le dans SharePoint, puis exécutez l'application pour le tester.  
  
#### Pour tester l'application  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Enregistrer tout**.  
  
2.  Appuyez sur la touche F5 pour exécuter l'application.  
  
     L'application est compilée, et ses fonctionnalités sont déployées sur SharePoint puis activées.  
  
3.  Dans la barre de navigation rapide, sélectionnez le lien **Patients** pour afficher la liste des **Patients**.  
  
     Les noms de colonne dans la liste doivent correspondre à ceux que vous avez entrés dans l'onglet **Vues** dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
4.  Sélectionnez le lien **Ajouter un nouvel élément** pour créer une fiche d'informations patiente.  
  
5.  Entrez les informations dans les champs, puis cliquez sur le bouton **Enregistrer**.  
  
     La nouvelle entrée est affichée dans la liste.  
  
## Voir aussi  
 [Création de colonnes de sites, de types de contenu et de listes pour SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Comment : Créer un type de champ personnalisé](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [Types de contenu](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Columns](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  