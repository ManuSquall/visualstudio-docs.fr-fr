---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un programme d&#39;amor&#231;age personnalis&#233; pour afficher une invite de confidentialit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "déploiement ClickOnce, composants requis"
  - "dépendances (.NET Framework), package du programme d'amorçage personnalisé"
  - "déployer des applications (Visual Studio), composants requis personnalisés"
  - "composants requis (.NET Framework), package du programme d'amorçage personnalisé"
  - "déploiement Windows Installer, composants requis"
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un programme d&#39;amor&#231;age personnalis&#233; pour afficher une invite de confidentialit&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez configurer des applications ClickOnce de façon à ce qu'elles soient automatiquement mises à jour lorsque de nouvelles versions d'assemblys ou des assemblys comportant de nouvelles versions de fichiers sont disponibles.  Afin de vous assurer que vos clients acceptent ce comportement, vous pouvez afficher une invite de confidentialité à leur intention.  Ils peuvent ainsi choisir d'accorder l'autorisation de mise à jour automatique à l'application.  S'ils n'autorisent pas cette mise à jour automatique, l'installation n'est pas effectuée.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Visual Studio 2010.  
  
## Création d'une boîte de dialogue de consentement de mise à jour  
 Pour afficher une invite de confidentialité, créez une application qui demande à l'utilisateur de consentir aux mises à jour automatiques de l'application.  
  
#### Pour créer une boîte de dialogue de consentement  
  
1.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, cliquez sur **Windows**, puis sur **Application Windows Forms**.  
  
3.  Dans **Nom**, tapez BoîteDialogueConsentement, puis cliquez sur **OK**.  
  
4.  Dans le concepteur, cliquez sur le formulaire.  
  
5.  Dans la fenêtre **Propriétés**, remplacez la propriété **Text** par Boîte de dialogue de consentement de mise à jour.  
  
6.  Dans la **Boîte à outils**, développez **Tous les Windows Forms** et faites glisser un contrôle **Label** vers le formulaire.  
  
7.  Dans le concepteur, cliquez sur le contrôle Label.  
  
8.  Dans la fenêtre **Propriétés**, remplacez la propriété **Text** sous **Apparence** par le texte suivant :  
  
     L'application que vous allez installer recherche les mises à jour les plus récentes sur le Web.  En cliquant sur "J'accepte", vous autorisez l'application à rechercher et à installer automatiquement des mises à jour à partir d'Internet.  
  
9. Dans la **Boîte à outils**, faites glisser un contrôle **Checkbox** au milieu du formulaire.  
  
10. Dans la fenêtre **Propriétés**, remplacez la propriété **Text** sous **Disposition** par J'accepte.  
  
11. Dans la **Boîte à outils**, faites glisser un contrôle **Button** vers la partie inférieure gauche du formulaire.  
  
12. Dans la fenêtre **Propriétés**, remplacez la propriété **Text** sous **Disposition** par Continuer.  
  
13. Dans la fenêtre **Propriétés**, remplacez la propriété **\(Name\)** sous **Design** par ProceedButton.  
  
14. Dans la **Boîte à outils**, faites glisser un contrôle **Button** vers la partie inférieure droite du formulaire.  
  
15. Dans la fenêtre **Propriétés**, remplacez la propriété **Text** sous **Disposition** par Annuler.  
  
16. Dans la fenêtre **Propriétés**, remplacez la propriété **\(Name\)** sous **Design** par CancelButton.  
  
17. Dans le concepteur, double\-cliquez sur la case à cocher **J'accepte** pour générer le gestionnaire d'événements CheckedChanged.  
  
18. Dans le fichier de code Form1, ajoutez le code suivant pour le gestionnaire d'événements CheckedChanged.  
  
     [!code-cs[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. Mettez à jour le constructeur de classe afin de désactiver le bouton **Continuer** par défaut.  
  
     [!code-cs[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. Dans le fichier de code Form1, ajoutez le code suivant pour une variable booléenne permettant de déterminer si l'utilisateur final a consenti aux mises à jour en ligne.  
  
     [!code-cs[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. Dans le concepteur, double\-cliquez sur le bouton **Continuer** pour générer le gestionnaire d'événements Click.  
  
22. Dans le fichier de code Form1, ajoutez le code suivant au gestionnaire d'événements Click pour le bouton **Continuer**.  
  
     [!code-cs[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. Dans le concepteur, double\-cliquez sur le bouton **Annuler** pour générer le gestionnaire d'événements Click.  
  
24. Dans le fichier de code Form1, ajoutez le code suivant au gestionnaire d'événements Click pour le bouton **Annuler**.  
  
     [!code-cs[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. Mettez à jour l'application afin qu'elle retourne une erreur si l'utilisateur final ne consent pas aux mises à jour en ligne.  
  
     Pour les développeurs Visual Basic uniquement :  
  
    1.  Dans l'**Explorateur de solutions**, cliquez sur **BoîteDialogueConsentement**.  
  
    2.  Dans le menu **Projet**, cliquez sur **Ajouter un module**, puis sur **Ajouter**.  
  
    3.  Dans le fichier de code Module1.vb, ajoutez le code suivant.  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  Dans le menu **Projet**, cliquez sur **Propriétés BoîteDialogueConsentement**, puis cliquez sur l'onglet **Application**.  
  
    5.  Désactivez **Activer l'infrastructure de l'application**.  
  
    6.  Dans le menu déroulant **Objet de démarrage**, sélectionnez **Module1**.  
  
        > [!NOTE]
        >  La désactivation de l'infrastructure de l'application désactive des fonctionnalités telles que les styles visuels Windows XP, les événements d'application, l'écran de démarrage, l'application à instance unique, etc.  Pour plus d'informations, consultez [Page Application, Concepteur de projets \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
     Pour les développeurs Visual C\# uniquement :  
  
     Ouvrez le fichier de code Program.cs et ajoutez le code suivant.  
  
     [!code-cs[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
## Création du package du programme d'amorçage personnalisé  
 Pour afficher l'invite de confidentialité destinée aux utilisateurs finaux, vous pouvez créer un package du programme d'amorçage personnalisé pour l'application de la boîte de dialogue de consentement de mise à jour et l'inclure en tant que composant requis dans toutes vos applications ClickOnce.  
  
 Cette procédure montre comment créer un package du programme d'amorçage personnalisé en créant les documents suivants :  
  
-   Un fichier manifeste product.xml pour décrire le contenu du programme d'amorçage.  
  
-   Un fichier manifeste package.xml pour répertorier les aspects spécifiques à la localisation de votre package, tels que les chaînes et les termes du contrat de licence.  
  
-   Un document pour les termes du contrat de licence.  
  
#### Étape 1 : Pour créer le répertoire du programme d'amorçage  
  
1.  Créez un répertoire nommé UpdateConsentDialog dans %PROGRAMFILES%\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
    > [!NOTE]
    >  Il se peut que vous deviez disposer des privilèges d'administrateur pour créer ce dossier.  
  
2.  Dans le répertoire UpdateConsentDialog, créez un sous\-répertoire nommé en.  
  
    > [!NOTE]
    >  Créez un répertoire pour chaque paramètre régional.  Par exemple, vous pouvez ajouter des sous\-répertoires pour les paramètres régionaux fr et de.  Ces répertoires contiendront les chaînes et modules linguistiques du français et de l'allemand, si nécessaire.  
  
#### Étape2 : pour créer le fichier manifeste product.xml  
  
1.  Créez un fichier texte appelé `product.xml`.  
  
2.  Dans le fichier product.xml, ajoutez le code XML suivant.  Veillez à ne pas remplacer le code XML existant.  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3.  Enregistrez le fichier dans le répertoire du programme d'amorçage UpdateConsentDialog.  
  
#### Étape 3 : pour créer le fichier manifeste package.xml et les termes du contrat de licence  
  
1.  Créez un fichier texte appelé `package.xml`.  
  
2.  Dans le fichier package.xml, ajoutez le code XML suivant pour définir les paramètres régionaux et inclure les termes du contrat de licence.  Veillez à ne pas remplacer le code XML existant.  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3.  Enregistrez le fichier dans le sous\-répertoire en, dans le répertoire du programme d'amorçage UpdateConsentDialog.  
  
4.  Créez un document appelé eula.rtf pour les termes du contrat de licence logiciel.  
  
    > [!NOTE]
    >  Les termes du contrat de licence logiciel doivent inclure les informations relatives aux licences, garanties, responsabilités et réglementations régionales en vigueur.  Ces fichiers doivent être spécifiques aux paramètres régionaux ; vous devez donc vous assurer que le fichier est enregistré dans un format qui prend en charge les caractères MBCS ou UNICODE.  Consultez votre service juridique sur le contenu des termes du contrat de licence logiciel.  
  
5.  Enregistrez le document dans le sous\-répertoire en, dans le répertoire du programme d'amorçage UpdateConsentDialog.  
  
6.  Si nécessaire, créez un nouveau fichier manifeste package.xml et un nouveau document eula.rtf pour les termes du contrat de licence logiciel pour chaque paramètre régional.  Par exemple, si vous avez créé des sous\-répertoires pour les paramètres régionaux fr et de, créez des fichiers manifeste package.xml et des termes de contrat de licence distincts, puis enregistrez\-les dans les sous\-répertoires fr et de.  
  
## Définition de l'application de consentement de mise à jour en tant que composant requis  
 Dans Visual Studio, vous pouvez définir l'application de consentement de mise à jour en tant que composant requis.  
  
#### Pour définir l'application de consentement de mise à jour en tant que composant requis  
  
1.  Dans l'**Explorateur de solutions**, cliquez sur le nom de l'application que vous voulez déployer.  
  
2.  Dans le menu **Projet**, cliquez sur **Propriétés de** *NomProjet*.  
  
3.  Cliquez sur la page **Publier**, puis sur **Composants requis**.  
  
4.  Sélectionnez **Boîte de dialogue de consentement de mise à jour**.  
  
    > [!NOTE]
    >  Vous devrez peut\-être fermer et rouvrir Visual Studio pour afficher la Boîte de dialogue de consentement de mise à jour dans la boîte de dialogue Composants requis.  
  
5.  Cliquez sur **OK**.  
  
## Création et test du programme d'installation  
 Après avoir défini l'application de consentement de mise à jour en tant que composant requis, vous pouvez générer le programme d'installation et le programme d'amorçage pour votre application.  
  
#### Pour créer et tester le programme d'installation sans cliquer sur J'accepte  
  
1.  Dans l'**Explorateur de solutions**, cliquez sur le nom de l'application que vous voulez déployer.  
  
2.  Dans le menu **Projet**, cliquez sur **Propriétés de** *NomProjet*.  
  
3.  Cliquez sur la page **Publier**, puis sur **Publier maintenant.**  
  
4.  Si la sortie publiée ne s'ouvre pas automatiquement, naviguez jusqu'à celle\-ci.  
  
5.  Exécutez le programme Setup.exe.  
  
     Le programme d'installation affiche le contrat de licence logiciel de la Boîte de dialogue de consentement de mise à jour.  
  
6.  Lisez le contrat de licence logiciel, puis cliquez sur **Accepter**.  
  
     L'application Boîte de dialogue de consentement de mise à jour s'affiche avec le texte suivant : L'application que vous allez installer recherche les mises à jour les plus récentes sur le Web.  En cliquant sur J'accepte, vous autorisez l'application à rechercher des mises à jour automatiquement sur Internet.  
  
7.  Fermez l'application ou cliquez sur Annuler.  
  
     L'application affiche une erreur : Une erreur s'est produite lors de l'installation des composants systèmes pour *NomApplication*.  Le programme d'installation ne peut pas continuer tant que tous les composants système n'ont pas été correctement installés.  
  
8.  Cliquez sur Détails pour afficher le message d'erreur suivant : L'installation du composant Boîte de dialogue de consentement de mise à jour a échoué avec le message d'erreur suivant : "L'accord de mise à jour automatique n'a pas été accepté." Les composants suivants n'ont pas été installés : \- Boîte de dialogue de consentement de mise à jour  
  
9. Cliquez sur **Fermer**.  
  
#### Pour créer et tester le programme d'installation en cliquant sur J'accepte  
  
1.  Dans l'**Explorateur de solutions**, cliquez sur le nom de l'application que vous voulez déployer.  
  
2.  Dans le menu **Projet**, cliquez sur **Propriétés de** *NomProjet*.  
  
3.  Cliquez sur la page **Publier**, puis sur **Publier maintenant.**  
  
4.  Si la sortie publiée ne s'ouvre pas automatiquement, naviguez jusqu'à celle\-ci.  
  
5.  Exécutez le programme Setup.exe.  
  
     Le programme d'installation affiche le contrat de licence logiciel de la Boîte de dialogue de consentement de mise à jour.  
  
6.  Lisez le contrat de licence logiciel, puis cliquez sur **Accepter**.  
  
     L'application Boîte de dialogue de consentement de mise à jour s'affiche avec le texte suivant : L'application que vous allez installer recherche les mises à jour les plus récentes sur le Web.  En cliquant sur J'accepte, vous autorisez l'application à rechercher des mises à jour automatiquement sur Internet.  
  
7.  Cliquez sur **J'accepte**, puis sur **Continuer**.  
  
     L'installation de l'application démarre.  
  
8.  Si la boîte de dialogue d'installation d'application apparaît, cliquez sur **Installer**.  
  
## Voir aussi  
 [Composants requis pour le déploiement d'applications](../deployment/application-deployment-prerequisites.md)   
 [Création de packages de programme d'amorçage](../deployment/creating-bootstrapper-packages.md)   
 [Comment : créer un manifeste de produit](../deployment/how-to-create-a-product-manifest.md)   
 [Comment : créer un manifeste de package](../deployment/how-to-create-a-package-manifest.md)   
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)