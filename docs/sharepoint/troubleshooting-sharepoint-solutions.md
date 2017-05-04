---
caps.handback.revision: 41
---
# D&#233;pannage des solutions SharePoint
  Les alertes ou problèmes suivants peuvent se produire lorsque vous déboguez des solutions SharePoint à l'aide de la  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]débogueur.  Pour plus d'informations, consultez  [NIB: Debugging SharePoint 2007 Workflow Solutions](http://msdn.microsoft.com/fr-fr/3a5392f3-66f3-48be-956e-02de23fa6247).  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## Restrictions de jetons dans sandbox WebParts Visual  
 Visual WebPart dans les solutions en sandbox ne peut pas traiter les jetons standard, tels que $SPUrl, qui prend en charge de l'exécution de SharePoint.  Par conséquent, l'URL n'est pas résolue, et vous ne pouvez pas prévisualiser le contenu en mode Design dans le Concepteur de composants visual web si vous y faire directement dans un élément script, comme dans l'exemple suivant :  
  
```  
<script src=”<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 Pour contourner cette limitation et de résoudre le jeton, faire à l'aide de littéraux :  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## Restrictions de caractères dans les noms de projets et d'éléments de projet  
 Noms de projets et d'éléments de projet peuvent contenir uniquement des caractères qui sont valides dans un chemin de déploiement dans SharePoint 2010.  Aucun autre caractère est autorisé.  
  
### Message d'erreur  
 Message d'erreur « Caractères non valides ».  
  
### Résolution  
 Pour les noms de projets SharePoint et les éléments de projet, utilisez uniquement les caractères suivants :  
  
-   Caractères ASCII alphanumériques  
  
-   Espace  
  
-   Point \(.\)  
  
-   Virgule \(\)  
  
-   Un trait de soulignement \(\_\)  
  
-   Tiret \(\-\)  
  
-   La barre oblique inverse \(\\\)  
  
 Lorsqu'un projet est empaqueté, une règle de validation vérifie que la propriété chemin de déploiement pour chaque fichier que vous déployiez contienne uniquement ces caractères valides.  
  
## Erreurs lors de la création de champs personnalisés  
 Dans  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], les champs personnalisés sont définis dans XML.  Erreurs peuvent se produire si un champ n'est pas défini ou référencé à l'aide d'un format spécifique.  
  
### Message d'erreur  
 Message d'erreur « Caractères non valides » au moment de l'emballage.  
  
### Résolution  
 L'ID d'une définition de champ doit être un GUID entouré accolades, comme le montre l'exemple suivant :  
  
```  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 Comme dans l'exemple suivant, une référence de champ dans un type de contenu doit être définie en utilisant le format d'élément vide \(\< FieldRef \/ \>\), ne pas en utilisant les éléments de début et de fin \(\< FieldRef \>\< \/ FieldRef \>\) :  
  
```  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 Si le code XML source du champ est incorrecte, n'est pas un fichier XML valide ou présente un autre problème, l'erreur « Impossible d'analyser fichier » se produit.  
  
## Nouvelles définitions de Site Non anglaises ne s'affichent pas dans la Page de création de Site après le déploiement  
 Une fois que vous créez et déployez une définition de site à l'aide d'une version non anglaise de  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\(autrement dit, une version avec un paramètre régional  [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]autre que 1033\), la   **Personnalisations de SharePoint** onglet n'apparaît pas dans le  **Sélection du modèle** boîte et le nouveau modèle de site ne s'affiche pas dans le  **Nouveau SharePoint Site** page.  
  
### Message d'erreur  
 Aucun.  
  
### Résolution  
 Ce problème se produit en raison d'une valeur incorrecte dans le  **chemin d'accès** propriété pour le fichier de configuration de la définition de site webtemp, tel que webtemp\_SiteDefinitionProject1.xml.  Dans le  **chemin d'accès** propriété pour le fichier webtemp, situé sous le  **Emplacement de déploiement**, remplacez 1033 par les paramètres régionaux  [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)].  Par exemple, pour utiliser un paramètre régional japonais modifier la valeur par 1041.  Pour plus d'informations, consultez  [ID de paramètres régionaux assignés par Microsoft](http://go.microsoft.com/fwlink/?LinkID=165561) sur le site Web MSDN.  
  
## Erreur s'affiche lorsqu'un projet de flux de travail est déployé sur un système propre  
 Ce problème se produit si vous déployez un projet de flux de travail dans  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]sur un système vierge.  Un système propre est un ordinateur qui dispose d'une nouvelle installation de  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]et SharePoint, mais aucun projet de flux de travail déployé.  
  
### Message d'erreur  
 Impossible de trouver la liste SharePoint : Historique du flux de travail.  
  
### Résolution  
 Cette erreur se produit en raison d'un historique de flux de travail manquant.  Étant donné que l'environnement de développement est un système propre, aucun flux de travail n'est déployés et l'historique de flux de travail n'existe pas encore.  Pour résoudre ce problème, rouvrez l'Assistant flux de travail, ce qui provoque l'historique du flux de travail à créer.  
  
##### Pour entrer de nouveau l'Assistant flux de travail  
  
1.  Dans  **L'Explorateur de solutions**, cliquez sur le nœud du flux de travail.  
  
2.  Dans le  **Propriétés** fenêtre, cliquez sur le bouton de sélection \(...\) sur toute propriété qui a un bouton de sélection.  
  
## L'utilisateur doit actualiser la Page dans le navigateur de l'Application pendant le débogage en mode de mise à jour Image  
 Si vous déboguez une solution SharePoint qui contient une page d'application avec un contrôle qui affiche une image, tel qu'un  [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)]contrôle d'Image, vous devez actualiser la page dans le navigateur pour afficher toutes les modifications ont été apportées à l'image.  
  
## Erreur : L'emplacement du Site n'est pas valide  
 Ce problème peut se produire si  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]n'est pas installé.  Il peut également se produire si vous n'avez pas l'accès administrateur au site SharePoint Web qui est spécifié dans le  **Assistant Personnalisation de SharePoint**.  
  
### Message d'erreur  
  
-   Emplacement du site SharePoint n'est pas valide.  
  
### Résolution  
  
-   Installation de  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
-   Vérifiez que vous disposez des droits d'accès administrateur pour le site SharePoint Web.  Pour plus d'informations, consultez le  [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)]l'article en ligne   [accorder l'accès au site portail](http://go.microsoft.com/fwlink/?LinkId=98310).  
  
## Événement de Web de suppression de site ne se produit pas dans le projet de récepteur d'événements  
 Lorsque vous créez un projet de récepteur d'événements et vous sélectionnez certains événements Web comme « un site est supprimé » l'événement ne se produit jamais.  
  
### Message d'erreur  
 Aucun.  
  
### Résolution  
 Ce problème se produit car la portée de fonctionnalité doit être « Site » pour gérer des événements au niveau du site, mais la valeur par défaut pour les projets de récepteur d'événements étendue de la fonctionnalité est « Web ».  Les événements Web concernés sont :  
  
-   Un site est en cours de suppression \(WebDeleting\)  
  
-   Un site a été supprimé \(WebDeleted\)  
  
-   Un site est en cours de déplacement \(WebMoving\)  
  
-   Un site a été déplacé \(WebMoved\)  
  
 Pour résoudre ce problème, modifiez la portée de fonctionnalité du récepteur d'événements, comme suit :  
  
##### Pour modifier la portée de fonctionnalité du récepteur d'événements  
  
1.  Dans  **L'Explorateur de solutions**, d'ouvrir le fichier .feature du récepteur d'événements dans le  **Concepteur de fonctionnalités** en double\-cliquant sur le fichier ou ouvrir son menu contextuel, puis choisissez  **Ouvrir**.  
  
2.  Cliquez sur la flèche à côté  **étendue de**, puis cliquez sur  **Site** dans la liste qui s'affiche.  
  
## Erreur de déploiement s'affiche après que le nom d'un identificateur dans un projet de modèle de connectivité de données métiers est modifié  
 Ce problème se produit si vous modifiez le nom de l'identificateur d'une entité dans un modèle de connectivité de données métiers \(BDC\) et que vous essayez ensuite de déployer la solution.  
  
### Messages d'erreur  
  
-   \<*nom de modèle*\> a les erreurs d'activation de Type de contenu externe suivantes...  
  
-   L'objet IMetadataObject portant le nom ' \<*nom de modèle*\>' a la valeur du champ « name » qui est dupliquée...  
  
### Résolution  
 Pour résoudre ce problème, supprimez le modèle manuellement, puis redéployer la solution.  Vous pouvez supprimer le modèle à l'aide des outils suivants :  
  
-   Administration centrale de SharePoint 2010.  Pour plus d'informations, consultez  [Gérer les modèles BDC](http://go.microsoft.com/fwlink/?LinkID=181472) sur le site Web Microsoft TechNet.  
  
-   Windows PowerShell.  Vous pouvez supprimer le modèle en tapant cette commande à l'invite de commande : **Remove\-SPBusinessDataCatalogModel**.  Pour plus d'informations, consultez  [applets de commande générales \(SharePoint Server 2010\)](http://go.microsoft.com/fwlink/?LinkID=182375) sur le site Web Microsoft TechNet.  
  
## Une erreur s'affiche lorsque vous essayez d'afficher un composant Visual Web Part dans SharePoint  
 Ce problème se produit lors de la  **chemin d'accès** propriété du contrôle utilisateur ne commence pas par la chaîne « CONTROLTEMPLATES\\ ».  
  
### Messages d'erreur  
  
-   Le fichier ' \/\_CONTROLTEMPLATES\/*\< nom du projet \>*\/*\< nom du composant WebPart \>*\/*\< nom du contrôle utilisateur \>*.ascx » n'existe pas.  
  
-   Erreur serveur dans « \/ » Application.  
  
### Résolution  
  
##### Pour résoudre ce problème  
  
1.  Dans  **L'Explorateur de solutions**, choisissez le fichier de contrôle utilisateur, dont l'extension est .ascx.  
  
2.  Dans la barre de menus, cliquez sur  **mode**,  **Fenêtre Propriétés**.  
  
3.  Dans le  **Propriétés** fenêtre, développez le  **Emplacement de déploiement** nœud.  
  
4.  Assurez\-vous que la valeur de la  **chemin d'accès** propriété commence par la chaîne « CONTROLTEMPLATES\\ ».  
  
## Erreur apparaît lorsqu'un flux de travail réutilisable importé qui contient un champ de formulaire tâche est exécuté  
 Ce problème se produit si vous importez un flux de travail qui contient un formulaire de tâche qui a un champ, puis exécutez le nouveau flux de travail sur le même système que celui à partir duquel vous l'avez importé.  
  
### Message d'erreur  
 Erreur lors de l'étape de déploiement « Activer les fonctionnalités » : Le champ portant l'Id *Guid*\] défini dans la fonctionnalité \[*Guid*\] a été trouvé dans la collection de sites actuelle ou dans un sous\-site.  
  
### Résolution  
 Cette erreur résulte de collisions d'ID champ qui se produisent parce que le flux de travail réutilisable importation de projet dans  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ne modifie pas l'ID du champ de formulaire tâche.  Si vous déployez un workflow importé sur le même serveur qui contient le flux de travail d'origine, se produit des collisions d'ID champ.  
  
 Pour résoudre ce problème, utilisez la fonctionnalité Rechercher et remplacer pour modifier la valeur de l'attribut ID de champ dans tous les fichiers de flux de travail importé.  
  
## Erreur s'affiche lorsqu'un importée renommée liste Instance est exécutée.  
 Ce problème se produit si vous renommez une instance de liste importée, puis l'exécutez dans  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
### Message d'erreur  
 Erreur de build : Erreur lors de l'étape de déploiement « Activer les fonctionnalités » : Le fichier Template\\Features\\ *import project* *feature* *name*\] \\Files\\Lists\\ \[*old* *list name*\] \\Schema.xml n'existe pas.  
  
### Résolution  
 Lorsque vous importez une instance de liste, un attribut nommé CustomSchema est ajouté au fichier Elements.xml de l'instance de liste.  Le fichier Elements.XML inclut le chemin d'accès d'un fichier schema.xml personnalisé pour l'instance de liste.  Lorsque vous renommez l'instance de liste dans  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], le chemin de déploiement pour le fichier schema.xml personnalisé change, mais la valeur de chemin d'accès de l'attribut CustomSchema n'est pas mis à jour.  Par conséquent, l'instance de liste ne peut pas trouver le fichier schema.xml dans l'ancien chemin d'accès est spécifié par l'attribut CustomSchema lorsque la fonctionnalité est activée.  
  
 Pour résoudre ce problème, mettez à jour le chemin d'accès de l'emplacement de déploiement du fichier schema.xml dans l'attribut CustomSchema.  
  
## Session interrompue par IIS de débogage SharePoint  
 Ce problème se produit si vous définissez un point d'arrêt dans un  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]solution SharePoint, cliquez sur la touche F5 pour l'exécuter et restent ensuite à un point d'arrêt est supérieure à 90 secondes.  
  
### Message d'erreur  
 Le processus de serveur Web débogué a été arrêté par Internet Information Services \(IIS\).  Vous pouvez éviter ce problème en configurant les paramètres ping du Pool d'applications dans IIS.  Consultez l'aide pour plus de détails.  
  
### Résolution  
 Par défaut, le pool d'applications IIS attend 90 secondes pour une application de répondre avant la fermeture de l'application.  Ce processus est appelé « envoyer un ping » l'application.  Pour résoudre ce problème, vous pouvez augmenter le délai d'attente ou désactiver entièrement la commande ping.  
  
##### Pour accéder aux paramètres de pool d'applications IIS  
  
1.  Ouvrez le Gestionnaire des services IIS.  
  
2.  Dans les  **les connexions** volet, développez le nœud du serveur SharePoint et puis cliquez sur le  **Des Pools d'applications** nœud.  
  
3.  Sur le  **Des Pools d'applications** page, sélectionnez le pool d'applications SharePoint \(généralement « SharePoint \- 80"\), puis, dans le  **Actions** volet, choisissez la  **Paramètres avancés** lien.  
  
4.  Pour augmenter le temps d'attente avant l'expiration IIS, modifiez la valeur de  **Le temps de réponse Maximum Ping \(secondes\)** à une valeur qui est supérieure à 90 secondes.  
  
5.  Pour désactiver IIS exécutant la commande ping, définissez  **Ping activé** à  **False**.  
  
## Retrait automatique laisse les Instance de liste orpheline dans SharePoint  
 Ce problème se produit si vous effectuez les étapes suivantes.  
  
1.  Créer une définition de liste qui a une instance de liste dans  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Cliquez sur la touche F5 pour exécuter la solution.  
  
3.  Arrêtez le débogage ou fermez le site SharePoint.  
  
4.  Rouvrez le site SharePoint et ouvrez l'instance de liste.  
  
### Message d'erreur  
 Erreur serveur dans « \/ » Application.  
  
### Résolution  
 Cela se produit car lorsque vous fermez une session de débogage d'une solution SharePoint, le retrait automatique fonctionnalité supprime la solution.  Le retrait supprime la définition de liste de SharePoint mais ne supprime pas l'instance de la liste.  La définition de liste sous\-jacente est requise par l'instance de liste.  
  
 Pour résoudre ce problème, déployez la solution, sur la barre de menus, choisissez  **Build**,  **déploiement**. \(Ne pas de déboguer la solution en cliquant sur la touche F5\). Ensuite, supprimez l'instance de liste dans SharePoint.  
  
## La SharePoint Solution d'origine est remplacée par une Version exportée  
 Si vous exportez une solution SharePoint, importez la solution dans  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]et ensuite de déployer la solution vers le même site à partir duquel elle a été exportée, la solution SharePoint d'origine est remplacée.  Ce problème ne se produit pas si vous déployez la solution sur un serveur qui ne dispose pas de la solution d'origine est activée sur ce dernier.  
  
### Message d'erreur  
 Aucun.  
  
### Résolution  
 Pour éviter de remplacer une solution sur le site à partir duquel elle a été exportée, modifiez les GUID de SolutionID et les ID de fonctionnalité de toutes les fonctionnalités importées dans le  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]projet.  
  
## Erreur s'affiche lorsque le débogage commence  
 Lorsque vous commencez à déboguer une solution SharePoint dans Visual Studio, une erreur indique que Visual Studio n'a pas pu charger le fichier Web.config parce que la clé donnée n'était pas dans le dictionnaire.  
  
### Message d'erreur  
 N'a pas pu charger le fichier de configuration Web.config.  Vérifiez le fichier pour tous les éléments XML mal formés et essayez à nouveau.  L'erreur suivante s'est produite : La clé donnée n'était pas présente dans le dictionnaire.  
  
### Résolution  
 Pour résoudre ce problème, assurez\-vous que la valeur de la propriété URL du Site du projet SharePoint dans Visual Studio correspond à l'URL qui est affecté à la Zone par défaut pour les mappages des accès de substitution de l'application web.  Vous ne pouvez pas résoudre l'erreur à l'aide d'une autre zone, comme l'Intranet, pour l'URL.  Le site URL pour le projet et l'URL dans la zone par défaut doivent correspondre.  Pour accéder aux mappages des accès de substitution, ouvrez l'utilitaire Administration centrale de SharePoint 2010, cliquez sur le  **Gestion des applications** lien, puis, sous  **Applications Web**, cliquez sur le  **configurer les mappages des accès de substitution** lien.  Pour plus d'informations, consultez  [créer des zones pour les applications Web](http://go.microsoft.com/fwlink/?LinkId=192274).  
  
## Voir aussi  
 [Dépannage de la création de packages et du déploiement SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [Génération et débogage de solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)  
  
  