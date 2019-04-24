---
title: 'Procédure pas à pas : Création d’un programme d’amorçage personnalisé pour afficher l’invite de déclaration de confidentialité | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 153773d27d4f27a6987f7984955dde26b187b65e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116511"
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>Procédure pas à pas : Création d’un programme d’amorçage personnalisé pour afficher une invite de confidentialité
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez configurer des applications ClickOnce à mettre à jour automatiquement lorsque les assemblys avec des versions plus récentes de fichier et les versions d’assembly sont disponibles. Pour vous assurer que vos clients acceptent ce comportement, vous pouvez afficher une invite de confidentialité pour eux. Ensuite, ils peuvent choisir s’il faut accorder l’autorisation de l’application pour mettre à jour automatiquement. Si l’application n’est pas autorisée à mettre à jour automatiquement, il n’installe pas.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
- Visual Studio 2010.  
  
## <a name="creating-an-update-consent-dialog-box"></a>Création d’une boîte de dialogue de consentement de mise à jour  
 Pour afficher une invite de confidentialité, créez une application qui demande le lecteur à donner son consentement pour les mises à jour automatiques pour l’application.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Pour créer une boîte de dialogue de consentement  
  
1. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
2. Dans le **nouveau projet** boîte de dialogue, cliquez sur **Windows**, puis cliquez sur **WindowsFormsApplication**.  
  
3. Pour le **nom**, type **BoîteDialogueConsentement**, puis cliquez sur **OK**.  
  
4. Dans le concepteur, cliquez sur le formulaire.  
  
5. Dans le **propriétés** fenêtre, de modifier le **texte** propriété **boîte de dialogue de consentement de mise à jour**.  
  
6. Dans le **boîte à outils**, développez **tous les Windows Forms**et faites glisser un **étiquette** contrôle au formulaire.  
  
7. Dans le concepteur, cliquez sur le contrôle d’étiquette.  
  
8. Dans le **propriétés** fenêtre, de modifier le **texte** propriété sous **apparence** à ce qui suit :  
  
    L’application que vous êtes sur le point d’installation vérifie les dernières mises à jour sur le Web. En cliquant sur « J’accepte », vous autorisez l’application pour vérifier et installer automatiquement les mises à jour à partir d’Internet.  
  
9. Dans le **boîte à outils**, faites glisser un **case à cocher** contrôle au milieu de l’écran.  
  
10. Dans le **propriétés** fenêtre, de modifier le **texte** propriété sous **disposition** à **J’accepte**.  
  
11. Dans le **boîte à outils**, faites glisser un **bouton** contrôle à l’angle inférieur gauche du formulaire.  
  
12. Dans le **propriétés** fenêtre, de modifier le **texte** propriété sous **disposition** à **continuer**.  
  
13. Dans le **propriétés** fenêtre, de modifier le **(nom)** propriété sous **conception** à **par ProceedButton**.  
  
14. Dans le **boîte à outils**, faites glisser un **bouton** contrôle vers le bas à droite du formulaire.  
  
15. Dans le **propriétés** fenêtre, de modifier le **texte** propriété sous **disposition** à **Annuler**.  
  
16. Dans le **propriétés** fenêtre, de modifier le **(nom)** propriété sous **conception** à **CancelButton**.  
  
17. Dans le concepteur, double-cliquez sur le **J’accepte** case à cocher pour générer le Gestionnaire d’événements CheckedChanged.  
  
18. Dans le fichier de code Form1, ajoutez le code suivant pour le Gestionnaire d’événements CheckedChanged.  
  
     [!code-csharp[ConsentDialog#1](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#1)]
     [!code-vb[ConsentDialog#1](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#1)]  
  
19. Mettre à jour le constructeur de classe pour désactiver le **continuer** bouton par défaut.  
  
     [!code-csharp[ConsentDialog#6](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#6)]
     [!code-vb[ConsentDialog#6](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#6)]  
  
20. Dans le fichier de code Form1, ajoutez le code suivant pour une variable booléenne suivre si l’utilisateur final a donné son consentement pour les mises à jour en ligne.  
  
     [!code-csharp[ConsentDialog#3](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#3)]
     [!code-vb[ConsentDialog#3](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#3)]  
  
21. Dans le concepteur, double-cliquez sur le **continuer** bouton pour générer le Gestionnaire d’événements Click.  
  
22. Dans le fichier de code Form1, ajoutez le code suivant au gestionnaire d’événements Click pour le **continuer** bouton.  
  
     [!code-csharp[ConsentDialog#2](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#2)]
     [!code-vb[ConsentDialog#2](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#2)]  
  
23. Dans le concepteur, double-cliquez sur le **Annuler** bouton pour générer le Gestionnaire d’événements Click.  
  
24. Dans le fichier de code Form1, ajoutez le code suivant pour le Gestionnaire d’événements Click pour le **Annuler** bouton.  
  
     [!code-csharp[ConsentDialog#4](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#4)]
     [!code-vb[ConsentDialog#4](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#4)]  
  
25. Mettre à jour l’application pour retourner une erreur si l’utilisateur final ne consent pas aux mises à jour en ligne.  
  
     Pour les développeurs Visual Basic uniquement :  
  
    1. Dans **l’Explorateur de solutions**, cliquez sur **BoîteDialogueConsentement**.  
  
    2. Sur le **projet** menu, cliquez sur **ajouter un Module**, puis cliquez sur **ajouter**.  
  
    3. Dans le fichier de code Module1.vb, ajoutez le code suivant.  
  
        [!code-vb[ConsentDialog#7](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/module1.vb#7)]  
  
    4. Sur le **projet** menu, cliquez sur **Propriétés BoîteDialogueConsentement**, puis cliquez sur le **Application** onglet.  
  
    5. Décochez la case **activer l’infrastructure application**.  
  
    6. Dans le **objet de démarrage** menu déroulant, sélectionnez **Module1**.  
  
       > [!NOTE]
       >  La désactivation de l’infrastructure d’application désactive les fonctionnalités telles que les styles visuels Windows XP, les événements d’application, l’écran de démarrage, application à instance unique et bien plus encore. Pour plus d’informations, consultez [Page Application, Concepteur de projets (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
       Pour les développeurs Visual c# uniquement :  
  
       Ouvrez le fichier de code Program.cs et ajoutez le code suivant.  
  
       [!code-csharp[ConsentDialog#5](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/program.cs#5)]  
  
26. Sur le **Build** menu, cliquez sur **BuildSolution**.  
  
## <a name="creating-the-custom-bootstrapper-package"></a>Création du Package de programme d’amorçage personnalisé  
 Pour afficher l’invite de confidentialité aux utilisateurs finaux, vous pouvez créer un package de programme d’amorçage personnalisé pour l’application de la boîte de dialogue de consentement de mise à jour et incluez-le comme condition préalable dans toutes vos applications ClickOnce.  
  
 Cette procédure montre comment créer un package de programme d’amorçage personnalisé en créant les documents suivants :  
  
- Un fichier manifeste product.xml pour décrire le contenu du programme d’amorçage.  
  
- Un fichier manifeste package.xml pour répertorier les aspects spécifiques à la localisation de votre package, telles que des chaînes et les termes du contrat de licence de logiciel.  
  
- Un document pour les termes du contrat de licence de logiciel.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Étape 1 : Pour créer le répertoire du programme d’amorçage  
  
1. Créez un répertoire nommé **UpdateConsentDialog** dans %PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
    > [!NOTE]
    >  Vous devrez peut-être pas des privilèges d’administrateur pour créer ce dossier.  
  
2. Dans le répertoire UpdateConsentDialog, créez un sous-répertoire nommé fr.  
  
    > [!NOTE]
    >  Créez un nouveau répertoire pour chacun des paramètres régionaux. Par exemple, vous pouvez ajouter des sous-répertoires pour les paramètres régionaux fr et de. Ces répertoires contient les chaînes Français et allemand et les modules linguistiques, si nécessaire.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Étape 2 : Pour créer le fichier manifeste product.xml  
  
1. Créez un fichier texte appelé `product.xml`.  
  
2. Dans le fichier product.xml, ajoutez le code XML suivant. Veillez à ne pas remplacer le code XML existant.  
  
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
  
3. Enregistrez le fichier dans le répertoire du programme d’amorçage UpdateConsentDialog.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Étape 3 : Pour créer le fichier manifeste package.xml et les termes du contrat de licence de logiciel  
  
1. Créez un fichier texte appelé `package.xml`.  
  
2. Dans le fichier package.xml, ajoutez le code XML suivant pour définir les paramètres régionaux et inclure les termes du contrat de licence de logiciel. Veillez à ne pas remplacer le code XML existant.  
  
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
  
3. Enregistrez le fichier dans le sous-répertoire en dans le répertoire du programme d’amorçage UpdateConsentDialog.  
  
4. Créer un document appelé eula.rtf pour les termes du contrat de licence de logiciel.  
  
    > [!NOTE]
    >  Les termes du contrat de licence de logiciel doit inclure des informations sur les licences, garanties, passifs et lois locales. Ces fichiers doivent être spécifiques, assurez-vous que le fichier est enregistré dans un format qui prend en charge les caractères MBCS ou UNICODE. Consultez votre service juridique sur le contenu des termes du contrat de licence logiciel.  
  
5. Enregistrez le document dans le sous-répertoire en dans le répertoire du programme d’amorçage UpdateConsentDialog.  
  
6. Si nécessaire, créez un nouveau fichier manifeste package.xml et un nouveau document eula.rtf pour les termes du contrat de licence logiciel pour chacun des paramètres régionaux. Par exemple, si vous avez créé les sous-répertoires pour les paramètres régionaux fr et de, créer des fichiers manifeste package.xml distincts et les termes du contrat de licence de logiciel et les enregistrer dans les sous-répertoires fr et de.  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>Définition de l’Application de consentement de mise à jour comme condition préalable  
 Dans Visual Studio, vous pouvez définir l’application de consentement de mise à jour comme condition préalable.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Pour définir l’Application de consentement de mise à jour comme condition préalable  
  
1. Dans **l’Explorateur de solutions**, cliquez sur le nom de votre application que vous souhaitez déployer.  
  
2. Dans le menu **Projet**, cliquez sur **Propriétés** de *NomProjet*.  
  
3. Cliquez sur le **publier** page, puis cliquez sur **conditions préalables**.  
  
4. Sélectionnez **mettre à jour de la boîte de dialogue consentement**.  
  
    > [!NOTE]
    >  Vous devrez peut-être fermer et rouvrir Visual Studio pour afficher la boîte de dialogue de consentement mise à jour dans la boîte de dialogue composants requis.  
  
5. Cliquez sur **OK**.  
  
## <a name="creating-and-testing-the-setup-program"></a>Créer et tester le programme d’installation  
 Après avoir défini l’application de consentement de mise à jour comme condition préalable, vous pouvez générer le programme d’installation et le programme d’amorçage pour votre application.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Pour créer et tester le programme d’installation par ne pas en cliquant sur J’accepte  
  
1. Dans **l’Explorateur de solutions**, cliquez sur le nom de votre application que vous souhaitez déployer.  
  
2. Dans le menu **Projet**, cliquez sur **Propriétés** de *NomProjet*.  
  
3. Cliquez sur le **publier** page, puis cliquez sur **publier maintenant**.  
  
4. Si la sortie de publication ne s’ouvre pas automatiquement, accédez à la sortie de publication.  
  
5. Exécutez le programme Setup.exe.  
  
     Le programme d’installation affiche le contrat de licence de boîte de dialogue de consentement de mise à jour logicielle.  
  
6. Lisez le contrat de licence logiciel, puis cliquez sur **Accept**.  
  
     L’application de la boîte de dialogue de consentement de mise à jour apparaît et affiche le texte suivant : L’application que vous êtes sur le point d’installation vérifie les dernières mises à jour sur le Web. En cliquant sur J’accepte, vous autorisez l’application pour rechercher les mises à jour automatiquement sur Internet.  
  
7. Fermez l’application, ou cliquez sur Annuler.  
  
     L’application affiche une erreur : Une erreur s’est produite lors de l’installation des composants système pour *ApplicationName*. Le programme d’installation ne peut pas continuer jusqu'à ce que tous les composants système ont été correctement installés.  
  
8. Cliquez sur Détails pour afficher le message d’erreur suivant : Dialogue de consentement de mise à jour de composant n’a pas pu installer avec le message d’erreur suivant : « L’accord de mise à jour automatique n’est pas accepté. » Impossible d’installer les composants suivants :-boîte de dialogue de consentement de mise à jour  
  
9. Cliquez sur **Fermer**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Pour créer et tester le programme d’installation en cliquant sur J’accepte  
  
1. Dans **l’Explorateur de solutions**, cliquez sur le nom de votre application que vous souhaitez déployer.  
  
2. Dans le menu **Projet**, cliquez sur **Propriétés** de *NomProjet*.  
  
3. Cliquez sur le **publier** page, puis cliquez sur **publier maintenant**.  
  
4. Si la sortie de publication ne s’ouvre pas automatiquement, accédez à la sortie de publication.  
  
5. Exécutez le programme Setup.exe.  
  
     Le programme d’installation affiche le contrat de licence de boîte de dialogue de consentement de mise à jour logicielle.  
  
6. Lisez le contrat de licence logiciel, puis cliquez sur **Accept**.  
  
     L’application de la boîte de dialogue de consentement de mise à jour apparaît et affiche le texte suivant : L’application que vous êtes sur le point d’installation vérifie les dernières mises à jour sur le Web. En cliquant sur J’accepte, vous autorisez l’application pour rechercher les mises à jour automatiquement sur Internet.  
  
7. Cliquez sur **J’accepte**, puis cliquez sur **continuer**.  
  
     Démarrage de l’application à installer.  
  
8. Si la boîte de dialogue installation de l’Application s’affiche, cliquez sur **installer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Prérequis pour le déploiement d’applications](../deployment/application-deployment-prerequisites.md)   
 [Création de packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md)   
 [Guide pratique pour Créer un manifeste de produit](../deployment/how-to-create-a-product-manifest.md)   
 [Guide pratique pour Créer un manifeste de Package](../deployment/how-to-create-a-package-manifest.md)   
 [Informations de référence sur le schéma de produit et de package](../deployment/product-and-package-schema-reference.md)
