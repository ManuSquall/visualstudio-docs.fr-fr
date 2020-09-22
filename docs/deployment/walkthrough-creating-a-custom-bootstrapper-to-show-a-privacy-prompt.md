---
title: Créer un programme d’amorçage personnalisé avec une invite de confidentialité
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8fbb05fcfdb1a639855ca31e9574d3037559610
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809274"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>Procédure pas à pas : Créer un programme d’amorçage personnalisé avec une invite de confidentialité
Vous pouvez configurer des applications ClickOnce pour qu’elles soient automatiquement mises à jour lorsque des assemblys avec des versions de fichiers et des versions d’assembly plus récentes deviennent disponibles. Pour vous assurer que vos clients acceptent ce comportement, vous pouvez afficher une invite de confidentialité. Ils peuvent ensuite choisir d’accorder ou non l’autorisation de mise à jour automatique à l’application. Si l’application n’est pas autorisée à se mettre à jour automatiquement, elle ne s’installe pas.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Visual Studio 2010.

## <a name="create-an-update-consent-dialog-box"></a>Boîte de dialogue créer un consentement de mise à jour
 Pour afficher une invite de confidentialité, créez une application qui demande au lecteur de donner son consentement aux mises à jour automatiques de l’application.

#### <a name="to-create-a-consent-dialog-box"></a>Pour créer une boîte de dialogue de consentement

1. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

2. Dans la boîte de dialogue **nouveau projet** , cliquez sur **Windows**, puis sur **WindowsFormsApplication**.

3. Pour le **nom**, tapez **ConsentDialog**, puis cliquez sur **OK**.

4. Dans le concepteur, cliquez sur le formulaire.

5. Dans la fenêtre **Propriétés** , modifiez la propriété **Text** pour **mettre à jour la boîte de dialogue de consentement**.

6. Dans la **boîte à outils**, développez **tous les Windows Forms**, puis faites glisser un contrôle **label** vers le formulaire.

7. Dans le concepteur, cliquez sur le contrôle Label.

8. Dans la fenêtre **Propriétés** , affectez à la propriété **Text** sous **apparence** la valeur suivante :

    L’application que vous êtes sur le point d’installer recherche les dernières mises à jour sur le Web. En cliquant sur « J’accepte », vous autorisez l’application à rechercher et installer automatiquement les mises à jour à partir d’Internet.

9. Dans la **boîte à outils**, faites glisser un contrôle **CheckBox** au milieu du formulaire.

10. Dans la fenêtre **Propriétés** , remplacez la propriété **texte** sous **disposition** par **J’accepte**.

11. Dans la **boîte à outils**, faites glisser un contrôle **Button** vers le coin inférieur gauche du formulaire.

12. Dans la fenêtre **Propriétés** , modifiez la propriété **texte** sous **disposition** pour **Continuer**.

13. Dans la fenêtre **Propriétés** , modifiez la propriété **(nom)** sous **conception** en **ProceedButton**.

14. Dans la **boîte à outils**, faites glisser un contrôle **Button** vers le coin inférieur droit du formulaire.

15. Dans la fenêtre **Propriétés** , affectez à la propriété **Text** sous **disposition** la valeur **Annuler**.

16. Dans la fenêtre **Propriétés** , remplacez la valeur de la propriété **(Name)** de **Design** par **CancelButton**.

17. Dans le concepteur, double-cliquez sur la case à cocher **J’accepte** pour générer le gestionnaire d’événements CheckedChanged.

18. Dans le fichier de code Form1, ajoutez le code suivant pour le gestionnaire d’événements CheckedChanged.

     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]

19. Mettez à jour le constructeur de classe pour désactiver le bouton **Continuer** par défaut.

     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]

20. Dans le fichier de code Form1, ajoutez le code suivant pour une variable booléenne afin de déterminer si l’utilisateur final a consenti à des mises à jour en ligne.

     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]

21. Dans le concepteur, double-cliquez sur le bouton **Continuer** pour générer le gestionnaire d’événements Click.

22. Dans le fichier de code Form1, ajoutez le code suivant au gestionnaire d’événements Click pour le bouton **Continuer** .

     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]

23. Dans le concepteur, double-cliquez sur le bouton **Annuler** pour générer le gestionnaire d’événements Click.

24. Dans le fichier de code Form1, ajoutez le code suivant pour le gestionnaire d’événements Click pour le bouton **Annuler** .

     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]

25. Mettez à jour l’application pour qu’elle retourne une erreur si l’utilisateur final n’accepte pas les mises à jour en ligne.

     Pour les développeurs Visual Basic uniquement :

    1. Dans **Explorateur de solutions**, cliquez sur **ConsentDialog**.

    2. Dans le menu **projet** , cliquez sur **Ajouter un module**, puis sur **Ajouter**.

    3. Dans le fichier de code *Module1. vb* , ajoutez le code suivant.

        [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]

    4. Dans le menu **projet** , cliquez sur **Propriétés de ConsentDialog**, puis cliquez sur l’onglet **application** .

    5. Décochez **activer l’infrastructure**de l’application.

    6. Dans le menu déroulant **objet de démarrage** , sélectionnez **Module1**.

       > [!NOTE]
       > La désactivation de l’infrastructure d’application désactive les fonctionnalités telles que les styles visuels Windows XP, les événements d’application, l’écran de démarrage, l’application à instance unique, et bien plus encore. Pour plus d'informations, consultez [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

       Pour les développeurs Visual C# uniquement :

       Ouvrez le fichier de code *Program.cs* , puis ajoutez le code suivant.

       [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]

26. Dans le menu **générer** , cliquez sur **BuildSolution**.

## <a name="create-the-custom-bootstrapper-package"></a>Créer le package du programme d’amorçage personnalisé
 Pour afficher l’invite de confidentialité pour les utilisateurs finaux, vous pouvez créer un package de programme d’amorçage personnalisé pour l’application de la boîte de dialogue de consentement des mises à jour et l’inclure comme condition préalable dans toutes vos applications ClickOnce.

 Cette procédure montre comment créer un package de programme d’amorçage personnalisé en créant les documents suivants :

- *product.xml* fichier manifeste pour décrire le contenu du programme d’amorçage.

- Un fichier manifeste *package.xml* pour répertorier les aspects spécifiques à la localisation de votre package, tels que les chaînes et les termes du contrat de licence logicielle.

- Document pour les termes du contrat de licence logiciel.

#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Étape 1 : pour créer le répertoire du programme d’amorçage

1. Créez un répertoire nommé **UpdateConsentDialog** dans le dossier *%ProgramFiles%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*.

    > [!NOTE]
    > Vous pouvez avoir besoin de privilèges d’administrateur pour créer ce dossier.

2. Dans le répertoire *UpdateConsentDialog* , créez un sous- *répertoire nommé en*.

    > [!NOTE]
    > Créez un répertoire pour chaque paramètre régional. Par exemple, vous pouvez ajouter des sous-répertoires pour les paramètres fr et de paramètres régionaux. Ces répertoires contiennent les chaînes et les modules linguistiques français et allemands, si nécessaire.

#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Étape 2 : pour créer le fichier manifeste product.xml

1. Créez un fichier texte appelé *product.xml*.

2. Dans le fichier *product.xml* , ajoutez le code XML suivant. Veillez à ne pas remplacer le code XML existant.

    ```xml
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

#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Étape 3 : pour créer le fichier manifeste package.xml et les termes du contrat de licence logiciel

1. Créez un fichier texte appelé *package.xml*.

2. Dans le fichier *package.xml* , ajoutez le code XML suivant pour définir les paramètres régionaux et inclure les termes du contrat de licence logicielle. Veillez à ne pas remplacer le code XML existant.

    ```xml
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

3. Enregistrez le fichier dans le sous-répertoire en-dessous dans le répertoire du programme d’amorçage UpdateConsentDialog.

4. Créez un document nommé *EULA. rtf* pour les termes du contrat de licence logiciel.

    > [!NOTE]
    > Les termes du contrat de licence logiciel doivent inclure des informations sur les licences, les garanties, les responsabilités et les lois locales. Ces fichiers doivent être spécifiques aux paramètres régionaux. Assurez-vous que le fichier est enregistré dans un format qui prend en charge les caractères MBCS ou UNICODE. Consultez votre service juridique sur le contenu des termes du contrat de licence logicielle.

5. Enregistrez le document dans le sous-répertoire en-dessous dans le répertoire du programme d’amorçage *UpdateConsentDialog* .

6. Si nécessaire, créez un nouveau *package.xml* fichier manifeste et un nouveau document *EULA. rtf* pour les termes du contrat de licence logiciel pour chaque paramètre régional. Par exemple, si vous avez créé des sous-répertoires pour les paramètres fr et de paramètres régionaux, créez des fichiers manifeste de package.xml séparés et des termes du contrat de licence logicielle, puis enregistrez-les dans les sous-répertoires fr et de.

## <a name="set-the-update-consent-application-as-a-prerequisite"></a>Définir l’application de consentement de mise à jour comme condition préalable
 Dans Visual Studio, vous pouvez définir l’application de consentement de mise à jour comme condition préalable.

#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Pour définir l’application de consentement des mises à jour comme condition préalable

1. Dans **Explorateur de solutions**, cliquez sur le nom de l’application que vous souhaitez déployer.

2. Dans le menu **projet** , cliquez sur **Propriétés**de *NomProjet* .

3. Cliquez sur la page **publier** , puis sur **composants requis**.

4. Sélectionnez **mettre à jour la boîte de dialogue de consentement**.

    > [!NOTE]
    > Vous devrez peut-être fermer et rouvrir Visual Studio pour afficher la boîte de dialogue de consentement des mises à jour dans la boîte de dialogue composants requis.

5. Cliquez sur **OK**.

## <a name="create-and-test-the-setup-program"></a>Créer et tester le programme d’installation
 Une fois que vous avez défini l’application de consentement des mises à jour comme condition préalable, vous pouvez générer le programme d’installation et le programme d’amorçage pour votre application.

#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Pour créer et tester le programme d’installation en ne cliquant pas sur J’accepte

1. Dans **Explorateur de solutions**, cliquez sur le nom de l’application que vous souhaitez déployer.

2. Dans le menu **projet** , cliquez sur **Propriétés**de *NomProjet* .

3. Cliquez sur la page **publier** , puis cliquez sur **publier maintenant**.

4. Si la sortie de publication ne s’ouvre pas automatiquement, accédez à la sortie de publication.

5. Exécutez le programme *Setup.exe* .

     Le programme d’installation affiche le contrat de licence de logiciel de la boîte de dialogue de consentement des mises à jour.

6. Lisez le contrat de licence logicielle, puis cliquez sur **accepter**.

     L’application de la boîte de dialogue de consentement des mises à jour apparaît et affiche le texte suivant : l’application que vous êtes sur le point d’installer recherche les dernières mises à jour sur le Web. En cliquant sur J’accepte, vous autorisez l’application à rechercher des mises à jour automatiquement sur Internet.

7. Fermez l’application ou cliquez sur Annuler.

     L’application affiche une erreur : une erreur s’est produite lors de l’installation des composants système pour *applicationName*. Le programme d’installation ne peut pas continuer tant que tous les composants système n’ont pas été correctement installés.

8. Cliquez sur détails pour afficher le message d’erreur suivant : échec de l’installation de la boîte de dialogue de consentement des mises à jour de composants avec le message d’erreur suivant : « l’accord de mise à jour automatique n’est pas accepté ». Échec de l’installation des composants suivants :-boîte de dialogue de consentement de mise à jour

9. Cliquez sur **Fermer**.

#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Pour créer et tester le programme d’installation en cliquant sur J’accepte

1. Dans **Explorateur de solutions**, cliquez sur le nom de l’application que vous souhaitez déployer.

2. Dans le menu **projet** , cliquez sur **Propriétés**de *NomProjet* .

3. Cliquez sur la page **publier** , puis cliquez sur **publier maintenant**.

4. Si la sortie de publication ne s’ouvre pas automatiquement, accédez à la sortie de publication.

5. Exécutez le programme *Setup.exe* .

     Le programme d’installation affiche le contrat de licence de logiciel de la boîte de dialogue de consentement des mises à jour.

6. Lisez le contrat de licence logicielle, puis cliquez sur **accepter**.

     L’application de la boîte de dialogue de consentement des mises à jour apparaît et affiche le texte suivant : l’application que vous êtes sur le point d’installer recherche les dernières mises à jour sur le Web. En cliquant sur J’accepte, vous autorisez l’application à rechercher des mises à jour automatiquement sur Internet.

7. Cliquez sur **J’accepte**, puis sur **Continuer**.

     L’application commence à s’installer.

8. Si la boîte de dialogue installation de l’application s’affiche, cliquez sur **installer**.

## <a name="see-also"></a>Voir aussi
- [Prérequis pour le déploiement d’applications](../deployment/application-deployment-prerequisites.md)
- [Créer des packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md)
- [Guide pratique pour créer un manifeste de produit](../deployment/how-to-create-a-product-manifest.md)
- [Guide pratique pour créer un manifeste de package](../deployment/how-to-create-a-package-manifest.md)
- [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)