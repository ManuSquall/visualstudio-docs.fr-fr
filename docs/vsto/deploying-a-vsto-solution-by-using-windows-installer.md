---
title: Déploiement d’une solution VSTO à l’aide de Windows Installer
description: Découvrez comment déployer un complément ou une solution au niveau du document Microsoft Visual Studio Tools pour Office (VSTO) à l’aide d’un projet Visual Studio Installer.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/18/2010
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e49705c99801cd6e09f4bf6d9be3c411cc2c53e3
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846543"
---
# <a name="deploying-a-vsto-solution-using-windows-installer"></a>Déploiement d’une solution VSTO à l’aide de Windows Installer

## <a name="summary"></a>Résumé

Découvrez comment déployer un complément ou une solution au niveau du document Microsoft Visual Studio Tools pour Office (VSTO) à l’aide d’un projet Visual Studio Installer.

Wouter van Vugt, code avocat

Ted Pattison, Ted Pattison groupe

Cet article a été mis à jour par Microsoft avec l’autorisation des auteurs d’origine.

**S’applique à :** Visual Studio Tools pour Office, Microsoft Office Microsoft Visual Studio.

## <a name="overview"></a>Vue d'ensemble

Vous pouvez développer une solution VSTO et déployer la solution à l’aide d’un package Windows Installer. Cette discussion comprend les étapes de déploiement d’un complément Office simple.

## <a name="deployment-methods"></a>Méthodes de déploiement

ClickOnce peut facilement être utilisé pour créer des configurations pour vos compléments et solutions. Toutefois, il ne peut pas installer de compléments qui requièrent des privilèges d’administration tels que les compléments de niveau ordinateur.

Les compléments qui requièrent des privilèges d’administrateur peuvent être installés à l’aide de Windows Installer, mais ils nécessitent davantage d’efforts pour créer le programme d’installation.

Pour obtenir une vue d’ensemble de la façon de déployer une solution VSTO à l’aide de ClickOnce, consultez [déployer une solution Office à l’aide de ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Déploiement de solutions Office ciblant le runtime VSTO

Les packages ClickOnce et Windows Installer doivent effectuer les mêmes tâches rudimentaires lors de l’installation d’une solution Office.

1. Installez les composants requis sur l’ordinateur de l’utilisateur.
2. Déployez les composants spécifiques de la solution.
3. Pour les compléments, créez des entrées de registre.
4. Faites confiance à la solution pour lui permettre de s’exécuter.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Composants requis sur l’ordinateur cible

Voici la liste des logiciels qui doivent être installés sur l’ordinateur pour exécuter des solutions VSTO :

- Microsoft Office 2010 ou version ultérieure.
- Microsoft .NET Framework 4 ou version ultérieure.
- Microsoft Visual Studio 2010 Tools pour Office Runtime.
  Le Runtime fournit un environnement qui gère les compléments et les solutions au niveau du document. Une version du runtime est fournie avec Microsoft Office mais vous souhaiterez peut-être redistribuer une version spécifique avec votre complément.
- Assemblys PIA (Primary Interop Assembly) pour Microsoft Office, si vous n’utilisez pas de types Interop incorporés.
- Tous les assemblys d’utilitaires référencés par les projets.

### <a name="specific-components-for-the-solution"></a>Composants spécifiques de la solution

Le package d’installation doit installer ces composants sur l’ordinateur de l’utilisateur :

- Le document Microsoft Office, si vous créez une solution au niveau du document.
- L’assembly de personnalisation et les assemblys dont il a besoin.
- Composants supplémentaires tels que les fichiers de configuration.
- Manifeste d’application (. manifest).
- Le manifeste de déploiement (. VSTO).

### <a name="registry-entries-for-add-ins"></a>Entrées de Registre pour les compléments

Microsoft Office utilise des entrées de Registre pour rechercher et charger des compléments. Ces entrées de Registre doivent être créées dans le cadre du processus de déploiement. Pour plus d’informations sur ces entrées de Registre, consultez [Registry Entries for VSTO Add-ins](registry-entries-for-vsto-add-ins.md).

Les compléments Outlook qui affichent des zones de formulaire personnalisées nécessitent des entrées de Registre supplémentaires qui permettent d’identifier les zones de formulaire. Pour plus d’informations sur les entrées de Registre, consultez [entrées de Registre pour les zones de formulaire Outlook](registry-entries-for-vsto-add-ins.md#OutlookEntries).

Les solutions au niveau du document ne nécessitent aucune entrée de registre. Au lieu de cela, les propriétés à l’intérieur du document sont utilisées pour localiser la personnalisation. Pour plus d’informations sur ces propriétés, consultez [vue d’ensemble des propriétés de document personnalisé](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Approbation de la solution VSTO

Pour permettre l’exécution d’une personnalisation, une solution doit être approuvée par l’ordinateur. Le complément peut être approuvé en signant le manifeste avec un certificat, en créant une relation d’approbation avec une liste d’inclusion ou en l’installant dans un emplacement approuvé sur l’ordinateur.

Pour plus d’informations sur la façon d’obtenir un certificat pour la signature, consultez [déploiement ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md). Pour plus d’informations sur les solutions d’approbation, consultez [approbation des solutions Office à l’aide des listes d’inclusion](trusting-office-solutions-by-using-inclusion-lists.md). Vous pouvez ajouter une entrée de liste d’inclusion avec une action personnalisée dans votre fichier Windows Installer. Pour plus d’informations sur l’activation de la liste d’inclusion, consultez [Comment : configurer la sécurité de la liste d’inclusion](how-to-configure-inclusion-list-security.md).

Si aucune de ces options n’est utilisée, une invite d’approbation est présentée à l’utilisateur pour lui permettre de décider d’approuver ou non la solution.

Pour plus d’informations sur la sécurité liée aux solutions au niveau du document, consultez [octroi de niveaux de confiance à des documents](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Création d’un programme d’installation de base

Les modèles de projet d’installation et de déploiement sont inclus avec l’extension de [projets Microsoft Visual Studio installer](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) qui est disponible au téléchargement.

Pour créer un programme d’installation pour une solution Office, vous devez effectuer les tâches suivantes :

- Ajoutez les composants de la solution Office qui sera déployée.
- Pour les compléments de niveau application, configurez les clés de registre.
- Configurez les composants requis pour qu’ils puissent être installés sur les ordinateurs des utilisateurs finaux.
- Configurez des conditions de lancement pour vérifier que les composants requis sont disponibles. Les conditions de lancement peuvent être utilisées pour bloquer l’installation si toutes les conditions préalables requises ne sont pas installées.

La première étape consiste à créer le projet d’installation.

### <a name="to-create-the-addin-setup-project"></a>Pour créer le projet d’installation du complément

1. Ouvrez le projet Complément Office que vous souhaitez déployer. Pour cet exemple, nous utilisons un complément Excel appelé ExcelAddIn.
2. Avec le projet Office ouvert, dans le menu **fichier** , développez **Ajouter** , puis cliquez sur **nouveau projet** pour ajouter un nouveau projet.
::: moniker range="=vs-2017"
3. Dans la boîte de dialogue **Ajouter un nouveau projet** , développez **autres types de projets** dans **le volet types de projets** , développez **configuration et déploiement** , puis sélectionnez **Visual Studio installer**.
4. Dans le volet **modèles** , sélectionnez **projet d’installation** dans le groupe modèles **Visual Studio installés** .
::: moniker-end
::: moniker range="=vs-2019"
3. Dans la boîte de dialogue **Ajouter un nouveau projet** , sélectionnez le modèle **projet d’installation** .
4. Cliquez sur **Suivant**.
::: moniker-end

5. Dans la zone **nom** , tapez **OfficeAddInSetup**.
::: moniker range="=vs-2017"
6. Cliquez sur **ouvrir** pour créer le nouveau projet d’installation.
::: moniker-end
::: moniker range="=vs-2019"
6. Cliquez sur **créer** pour créer le nouveau projet d’installation.
::: moniker-end

Visual Studio ouvre l’Explorateur de système de fichiers pour le nouveau projet d’installation. L’Explorateur de système de fichiers vous permet d’ajouter des fichiers au projet d’installation.

   ![Capture d’écran de l’Explorateur de système de fichiers pour le projet d’installation](media/setup-project-figure-1.png)

   **Figure 1 : Explorateur du système de fichiers pour le projet d’installation**

Le projet d’installation doit déployer ExcelAddIn. Vous pouvez configurer le projet d’installation pour cette tâche en ajoutant la sortie du projet ExcelAddIn au projet d’installation.

### <a name="to-add-the-exceladdin-project-output"></a>Pour ajouter la sortie du projet ExcelAddIn

1. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur **OfficeAddInSetup**, cliquez sur **Ajouter** , puis sur **sortie du projet**.
2. Dans la boîte de dialogue **Ajouter un groupe de sorties de projet** , sélectionnez le **ExcelAddIn** dans la liste de projets et la **sortie principale**.
3. Cliquez sur **OK** pour ajouter la sortie du projet au projet d’installation.

    ![Capture d’écran de la boîte de dialogue Ajouter un groupe de sortie de projet](media/setup-project-figure-2.png)

    **Figure 2 : boîte de dialogue Ajouter un groupe de sortie du projet d’installation**

Le projet d’installation doit déployer le manifeste de déploiement et le manifeste d’application. Ajoutez ces deux fichiers au projet d’installation en tant que fichiers autonomes à partir du dossier de sortie du projet ExcelAddIn.

### <a name="to-add-the-deployment-and-application-manifests"></a>Pour ajouter les manifestes de déploiement et d’application

1. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur **OfficeAddInSetup**, cliquez sur **Ajouter**, puis sur **fichier**.
2. Dans la boîte de dialogue **Ajouter des fichiers** , accédez au répertoire de sortie **ExcelAddIn** . En général, le répertoire de sortie est le sous-dossier de la **\\ version bin** du répertoire racine du projet, selon la configuration de build sélectionnée.
3. Sélectionnez les fichiers **ExcelAddIn. vsto** et **ExcelAddIn.dll. manifest** , puis cliquez sur **ouvrir** pour ajouter ces deux fichiers au projet d’installation.

    ![Capture d’écran des manifestes d’application et de déploiement dans Explorateur de solutions](media/setup-project-figure-3.jpg)

    **Figure 3 : manifestes d’application et de déploiement du complément dans Explorateur de solutions**

Le référencement du ExcelAddIn comprend tous les composants requis par ExcelAddIn. Ces composants doivent être exclus et déployés à l’aide de packages requis pour permettre leur inscription correcte. En outre, les termes du contrat de licence logiciel doivent être affichés et acceptés avant le début de l’installation.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>Pour exclure les dépendances du projet ExcelAddIn

1. Dans le **Explorateur de solutions**, dans le **nœud OfficeAddInSetup** , sélectionnez tous les éléments de dépendance sous l’élément **Dépendances détectées** , à l’exception de **Microsoft .NET Framework** ou de tout assembly qui se termine par **\*.Utilities.dll**. Les assemblys des utilitaires sont conçus pour être déployés avec votre application.
2. Cliquez avec le bouton droit sur le groupe et sélectionnez **Propriétés**.
3. Dans la fenêtre **Propriétés** , remplacez la valeur de la propriété **exclure** par **true** pour exclure les assemblys dépendants du projet d’installation. Veillez à ne pas exclure les assemblys d’utilitaires.

    ![Capture d’écran de Explorateur de solutions montrant les dépendances à exclure](media/setup-project-figure-4.jpg)

    **Figure 4 : exclusion des dépendances**

Vous pouvez configurer votre package Windows Installer pour installer les composants requis en ajoutant un programme d’installation, également appelé programme d’amorçage. Ce programme d’installation peut installer les composants requis, un processus appelé amorçage.

Pour les **ExcelAddIn**, ces conditions préalables doivent être installées pour que le complément puisse s’exécuter correctement :

- Version de Microsoft .NET Framework ciblée par la solution Office.
- Microsoft Visual Studio 2010 Tools pour Office Runtime.

Pour configurer des composants dépendants comme composants requis

1. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **OfficeAddInSetup** et sélectionnez **Propriétés**.
2. La boîte de dialogue **pages de propriétés de OfficeAddInSetup** s’affiche.
3. Cliquez sur le bouton **composants requis** .
4. Dans la boîte de dialogue composants requis, sélectionnez la version appropriée du .NET Framework et le Microsoft Visual Studio Tools pour Office Runtime.

    ![Capture d’écran de la boîte de dialogue composants requis](media/setup-project-figure-5.png)

    **Figure 5 : boîte de dialogue composants requis**

    > [!NOTE]
    >Certains packages de composants requis configurés dans votre projet d’installation Visual Studio dépendent de la configuration de build sélectionnée. Vous devez sélectionner les composants requis appropriés pour chaque configuration de build que vous utilisez.

Microsoft Office localise les compléments à l’aide de clés de registre. Les clés de la ruche de l' \_ utilisateur actuel HKEY \_ sont utilisées pour inscrire le complément pour chaque utilisateur individuel. Les clés sous la \_ ruche HKEY local \_ machine sont utilisées pour inscrire le complément pour tous les utilisateurs de l’ordinateur. Pour plus d’informations sur les clés de Registre, consultez [Registry Entries for VSTO Add-ins](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Pour configurer le registre

1. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur **OfficeAddInSetup**.
2. Développez **affichage**.
3. Cliquez sur **Registre** pour ouvrir la fenêtre de l’éditeur du Registre.
4. Dans l’éditeur **du Registre (OfficeAddInSetup)** , développez **HKEY \_ local \_ machine** , puis **Software**.
5. Supprimez la clé **\[ Manufacturer \]**? située sous **HKEY \_ local \_ machine \\ Software**.
6. Développez **HKEY \_ Current \_ User** , puis **Software**.
7. Supprimez la clé de **\[ fabricant \]** trouvée sous **HKEY \_ Current \_ User \\ Software**.
8. Pour ajouter des clés de Registre pour l’installation du complément, cliquez avec le bouton droit sur la clé **Hive utilisateur/ordinateur** , puis sélectionnez **nouvelle clé**. Utilisez le **logiciel** texte comme nom de la nouvelle clé. Cliquez avec le bouton droit sur la clé de **logiciel** nouvellement créée et créez une nouvelle clé avec le texte **Microsoft**.
9. Utilisez un processus similaire pour créer l’intégralité de la hiérarchie de clés requise pour l’inscription du complément :

    **Logiciel Hive utilisateur/ \\ ordinateur \\ \\ \\ compléments Microsoft Office Excel \\ \\ clé SampleCompany. ExcelAddIn**

    Le nom de la société est souvent utilisé comme préfixe du nom du complément pour fournir une unicité.

10. Cliquez avec le bouton droit sur la clé **clé SampleCompany. ExcelAddIn** , sélectionnez **nouveau**, puis cliquez sur **valeur de chaîne**. Utilisez la **Description** du texte pour le nom.
11. Utilisez cette étape pour ajouter trois valeurs supplémentaires :
    - **FriendlyName** de type **chaîne**
    - **LoadBehavior** de type **DWORD**
    - **Manifeste** de type **chaîne**

12. Cliquez avec le bouton droit sur la valeur **Description** dans l’éditeur du Registre, puis cliquez sur **fenêtre Propriétés**. Dans la **fenêtre Propriétés**, entrez **complément de démonstration Excel** pour la propriété valeur.
13. Sélectionnez la clé **FriendlyName** dans l’éditeur du Registre. Dans la **fenêtre Propriétés**, remplacez la **valeur** de la propriété valeur par **complément de démonstration Excel**.
14. Dans l’éditeur du Registre, sélectionnez la clé **LoadBehavior** . Dans la **fenêtre Propriétés**, affectez à la propriété **valeur la valeur** **3.** La valeur 3 du LoadBehavior indique que le complément doit être chargé au démarrage de l’application hôte. Pour plus d’informations sur le comportement de chargement, consultez [entrées du Registre pour les compléments VSTO](registry-entries-for-vsto-add-ins.md).

15. Sélectionnez la clé de **manifeste** dans l’éditeur du Registre. Dans la **fenêtre Propriétés**, remplacez la **valeur** de la propriété valeur par **file:///[TARGETDIR] ExcelAddIn. vsto | vstolocal**

    ![Capture d’écran de l’éditeur du Registre](media/setup-project-figure-6.png)

    **Figure 6 : configuration des clés de Registre**

      Le runtime VSTO utilise cette clé de Registre pour localiser le manifeste de déploiement. La macro [TARGETDIR] sera remplacée par le dossier dans lequel le complément est installé. La macro inclura le caractère \ de fin, donc le nom de fichier du manifeste de déploiement doit être ExcelAddIn. vsto sans le caractère \.
      Le suffixe **vstolocal** indique au runtime VSTO que le complément doit être chargé à partir de cet emplacement au lieu du cache ClickOnce. La suppression de ce suffixe force le runtime à copier la personnalisation dans le cache ClickOnce.

   >[!WARNING]
   >Vous devez être très prudent avec l’éditeur du Registre dans Visual Studio. Par exemple, si vous avez accidentellement défini DeleteAtUninstall pour la mauvaise clé, vous risquez de supprimer une partie active du Registre, en laissant l’ordinateur de l’utilisateur dans un état d’interruption incohérent, voire pire.

les versions 64 bits d’Office utiliseront la ruche de Registre 64 bits pour rechercher des compléments. Pour inscrire des compléments sous la ruche de Registre 64 bits, la plateforme cible du projet d’installation doit être définie sur 64 bits uniquement.

1. Sélectionnez le projet **OfficeAddInSetup** dans l’Explorateur de solutions.
2. Accédez à la fenêtre **Propriétés** et affectez à la propriété **TargetPlatform** la valeur **x64**.

Si vous installez un complément pour les versions 32 bits et 64 bits d’Office, vous devez créer deux packages MSI distincts. Une pour 32 bits et une pour 64 bits.

  ![Capture d’écran de la fenêtre Propriétés montrant la plateforme cible pour l’inscription des compléments avec Office 64 bits](media/setup-project-figure-7.jpg)

  **Figure 7 : plateforme cible pour l’inscription des compléments avec Office 64 bits**

Si le package MSI est utilisé pour installer le complément ou la solution, il peut installer sans les composants requis en cours d’installation. Vous pouvez utiliser des conditions de lancement dans le MSI pour empêcher l’installation du complément si les conditions préalables ne sont pas installées.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Configurer une condition de lancement pour détecter le runtime VSTO

1. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur **OfficeAddInSetup**.
2. Développez **affichage**.
3. Cliquez sur **conditions de lancement**.
4. Dans l’éditeur des **conditions de lancement (OfficeAddInSetup)** , cliquez avec le bouton droit sur **Configuration requise sur l’ordinateur cible**, puis cliquez sur **Ajouter une condition de lancement du Registre**. Cette condition de recherche peut rechercher dans le registre une clé que le runtime VSTO installe. La valeur de la clé est ensuite disponible pour les différents éléments du programme d’installation par le biais d’une propriété nommée. La condition de lancement utilise la propriété définie par la condition de recherche pour rechercher une certaine valeur.
5. Dans l’éditeur des **conditions de lancement (OfficeAddInSetup)** , sélectionnez la condition **de recherche RegistryEntry1** , cliquez avec le bouton droit sur la condition, puis sélectionnez **fenêtre Propriétés**.

6. Dans la fenêtre **Propriétés** , définissez les propriétés suivantes :
   1. Définissez la valeur de **(nom)** sur **Rechercher le runtime VSTO 2010**.
   2. Remplacez la valeur de la **propriété** par **VSTORUNTIMEREDIST**.
   3. Définissez la valeur de **RegKey** sur **logiciel \\ Microsoft \\ VSTO Runtime Setup \\ v4R**
   4. Laissez la propriété **root** définie sur **vsdrrHKLM**.
   5. Remplacez la **valeur** de la propriété Value par **version**.

7. Dans l’éditeur des **conditions de lancement (OfficeAddInSetup)** , sélectionnez la condition de lancement **condition1** , cliquez avec le bouton droit sur la condition, puis sélectionnez **fenêtre Propriétés**.
8. Dans la fenêtre Propriétés, définissez les propriétés suivantes :
   1. Définissez le **(nom)** pour **Vérifier la disponibilité du runtime VSTO 2010**.
   2. Remplacez la valeur de la **condition** par **VSTORUNTIMEREDIST \> = "10.0.30319"**
   3. Laissez la propriété **InstallUrl** vide.
   4. Définir le **message** sur **le Runtime Visual Studio 2010 Tools pour Office n’est pas installé. Exécutez Setup.exe pour installer le complément**.

        ![Capture d’écran de la fenêtre de propriétés pour vérifier la condition de lancement de la disponibilité du Runtime](media/setup-project-figure-8.jpg)

        **Figure 8 : fenêtre Propriétés de la condition de lancement vérifier la disponibilité du Runtime**

 La condition de lancement ci-dessus vérifie explicitement la présence du runtime VSTO lorsqu’il est installé par le package du programme d’amorçage.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Configurer une condition de lancement pour détecter le runtime VSTO installé par Office

1. Dans l’éditeur des **conditions de lancement (OfficeAddInSetup)** , cliquez avec le bouton droit sur **ordinateur cible de recherche**, puis cliquez sur **Ajouter une recherche** dans le registre.
2. Sélectionnez la condition **de recherche RegistryEntry1** , cliquez avec le bouton droit sur la condition, puis sélectionnez **fenêtre Propriétés**.
3. Dans la fenêtre **Propriétés** , définissez les propriétés suivantes :
    1. Définissez la valeur de **(nom)** pour **Rechercher le runtime Office VSTO**.
    2. Remplacez la valeur de la **propriété** par **OfficeRuntime**.
    3. Définissez la valeur de **RegKey** sur **logiciel \\ Microsoft \\ VSTO Runtime Setup \\ v4**.
    4. Laissez la propriété **root** définie sur **vsdrrHKLM**.
    5. Remplacez la **valeur** de la propriété Value par **version**.

4. Dans l’éditeur des **conditions de lancement (OfficeAddInSetup)** , sélectionnez la condition de lancement vérifier la disponibilité de la **disponibilité du runtime VSTO 2010** définie précédemment, cliquez avec le bouton droit sur la condition, puis sélectionnez **fenêtre Propriétés**.

5. Modifiez la valeur de la propriété **condition** en **VSTORUNTIMEREDIST \> = "10.0.30319" ou OFFICERUNTIME \> = "10.0.21022"**. Les numéros de version sont peut-être différents selon les versions du runtime requises par votre complément.

    ![Capture d’écran des fenêtres de propriétés pour la condition de lancement](media/setup-project-figure-9.jpg)
  
    **Figure 9 : fenêtres de propriétés de la condition vérifier la disponibilité du runtime via Redist ou Office Launch**

Si un complément cible .NET Framework 4, ou plus récent, les types contenus dans les assemblys PIA (Primary Interop Assembly), qui sont référencés, peuvent être incorporés dans l’assembly VSTO.

Pour vérifier si les types Interop sont incorporés dans votre complément en effectuant les étapes suivantes :

1. Développez le nœud références dans Explorateur de solutions
2. Sélectionnez l’une des références d’assembly PIA, par exemple **Office**.
3. Affichez les fenêtres de propriétés en appuyant sur F4 ou en sélectionnant Propriétés dans le menu contextuel assemblys.
4. Vérifiez la valeur de la propriété **incorporer les types Interop**.

Si la valeur est définie sur **true**, les types sont incorporés et vous pouvez passer à la section [**pour générer le projet d’installation**](#to-build-the-setup-project) .

Pour plus d’informations, consultez [équivalence de type et types Interop incorporés](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Pour configurer des conditions de lancement pour détecter ce qui concerne les assemblys PIA Office

1. Dans l’éditeur des **conditions de lancement (OfficeAddInSetup)** , cliquez avec le bouton droit sur **Configuration requise sur l’ordinateur cible**, puis **cliquez sur Ajouter Windows Installer condition de lancement**. Cette condition de lancement recherche un assembly PIA Office en recherchant l’ID de composant spécifique.
2. Cliquez avec le bouton droit sur **Rechercher Composant1** , puis cliquez sur **fenêtre Propriétés** pour afficher les propriétés de la condition de lancement.
3. Dans la **fenêtre Propriétés**, définissez les propriétés suivantes :

    1. Modifiez la valeur de la propriété **(nom)** pour **Rechercher l’assembly PIA Office partagé**
    2. Modifiez la valeur de l' **ID de composant pour le** composant Office que vous utilisez. Vous pouvez trouver la liste des ID de composant dans le tableau ci-dessous, par exemple **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**.
    3. Modifiez la valeur de la propriété **Property** en **HASSHAREDPIA**.

4. Dans l’éditeur des **conditions de lancement (OfficeAddInSetup)** , cliquez avec le bouton droit sur **condition1** , puis cliquez sur **fenêtre Propriétés** pour afficher les propriétés de la condition de lancement.

5. Modifiez les propriétés de l' **condition1**:

    1. Modifiez le **(nom)** pour **Vérifier la disponibilité de l’assembly PIA partagé d’Office**.
    2. Modifiez la **condition** en **HASSHAREDPIA**.
    3. Laissez **InstallUrl** vide.
    4. La modification du **message** en **un composant requis pour l’interaction avec Excel n’est pas disponible. Exécutez setup.exe**.

    ![Capture d’écran de la fenêtre de propriétés pour la condition de lancement de l’assembly PIA Office partagé](media/setup-project-figure-10.jpg)
  
    **Figure 10 : fenêtre Propriétés de la condition de lancement vérifier les assemblys PIA partagés d’Office**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>ID de composant des assemblys PIA (Primary Interop Assembly) pour Microsoft Office

|Assembly PIA|Office 2010|Office 2013|Office 2013 (64 bits)|Office 2016|Office 2016 (64 bits)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B8022333E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Forms 2,0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|Balise active|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Office partagé|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|Project|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![Capture d’écran des conditions de lancement finales](media/setup-project-figure-11.jpg)

  **Figure 11 : conditions de lancement finales**

Vous pouvez affiner les conditions de lancement de l’installation de ExcelAddIn. Par exemple, il peut être utile de vérifier si l’application Office cible réelle est installée.

### <a name="to-build-the-setup-project"></a>Pour générer le projet d’installation

1. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **OfficeAddInSetup** , puis cliquez sur **générer**.
2. À l’aide de l' **Explorateur Windows**, accédez au répertoire de sortie du projet **OfficeAddInSetup** et accédez au dossier Release ou debug, en fonction de la configuration de build sélectionnée. Copiez tous les fichiers du dossier vers un emplacement accessible aux utilisateurs.

Pour tester l’installation de ExcelAddIn

1. Accédez à l’emplacement où vous avez copié **OfficeAddInSetup** .
2. Double-cliquez sur le fichier setup.exe pour installer le complément **OfficeAddInSetup** . Acceptez les termes du contrat de licence logiciel qui s’affichent, puis terminez l’Assistant Installation pour installer le complément sur l’ordinateur de l’utilisateur.

La solution Office Excel doit être installée et exécutée à partir de l’emplacement spécifié lors de l’installation.

## <a name="additional-requirements-for-document-level-solutions"></a>Exigences supplémentaires pour les solutions au niveau du document

Le déploiement de solutions au niveau du document nécessite quelques étapes de configuration différentes dans le projet d’installation Windows Installer.

Voici une liste des étapes de base requises pour déployer une solution au niveau du document :

- Créez le projet d’installation Visual Studio.
- Ajoutez la sortie principale de votre solution au niveau du document. La sortie principale comprend également le document Microsoft Office.
- Ajoutez les manifestes de déploiement et d’application en tant que fichiers libres.
- Excluez les composants dépendants du package d’installation (sauf pour tous les assemblys d’utilitaires).
- Configurez les packages requis.
- Configurer des conditions de lancement.
- Générez le projet d’installation et copiez les résultats dans l’emplacement de déploiement.
- Déployez la solution au niveau du document sur l’ordinateur de l’utilisateur en exécutant le programme d’installation.
- Mettez à jour les propriétés de document personnalisées si nécessaire.

### <a name="changing-the-location-of-the-deployed-document"></a>Modification de l’emplacement du document déployé

Les propriétés contenues dans un document Office sont utilisées pour rechercher des solutions au niveau du document. Si le document est installé dans le même dossier que l’assembly VSTO, aucune modification n’est requise. Toutefois, s’il est installé dans un dossier différent, ces propriétés devront être mises à jour pendant l’installation.

Pour plus d’informations sur ces propriétés de document, consultez [vue d’ensemble des propriétés de document personnalisé](custom-document-properties-overview.md).

Pour modifier ces propriétés, vous devez utiliser une action personnalisée au cours de l’installation.

L’exemple suivant utilise une solution au niveau du document appelée ExcelWorkbookProject et un projet d’installation nommé ExcelWorkbookSetup. Le projet ExcelWorkbookSetup est configuré à l’aide des mêmes étapes que celles décrites ci-dessus, à l’exception de la définition des clés de registre.

Pour ajouter le projet d’action personnalisée à votre solution Visual Studio

1. Ajoutez un nouveau projet de console .NET à la solution en cliquant avec le bouton droit sur le **projet de déploiement de document Office** dans le **Explorateur de solutions**
2. Développez **Ajouter** , puis cliquez sur **nouveau projet**.
3. Sélectionnez le modèle application console et nommez le projet **AddCustomizationCustomAction**.

    ![Capture d’écran de l’Explorateur de solutions-AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Figure 12 : Explorateur de solutions-AddCustomizationCustomAction**

4. Ajoutez une référence à ces assemblys :
    1. System.ComponentModel
    2. System.Configuration.Install
    3. Microsoft. VisualStudio. Tools. applications
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. Copiez ce code dans Program.cs ou Program. vb

```csharp
    using System;
    using System.IO;
    using System.Collections;
    using System.ComponentModel;
    using System.Configuration.Install;
    using Microsoft.VisualStudio.Tools.Applications;
    using Microsoft.VisualStudio.Tools.Applications.Runtime;

    namespace AddCustomizationCustomAction
    {
        [RunInstaller(true)]
        public class AddCustomizations : Installer
        {
            public AddCustomizations() : base() { }

            public override void Install(IDictionary savedState)
            {
                base.Install(savedState);

                //Get the CustomActionData Parameters
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;
                string assemblyLocation = Context.Parameters.ContainsKey("assemblyLocation") ? Context.Parameters["assemblyLocation"] : String.Empty;
                string deploymentManifestLocation = Context.Parameters.ContainsKey("deploymentManifestLocation") ? Context.Parameters["deploymentManifestLocation"] : String.Empty;
                Guid solutionID = Context.Parameters.ContainsKey("solutionID") ? new Guid(Context.Parameters["solutionID"]) : new Guid();

                string newDocLocation = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation));

                try
                {
                    //Move the file and set the Customizations
                    if (Uri.TryCreate(deploymentManifestLocation, UriKind.Absolute, out Uri docManifestLocationUri))
                    {
                        File.Move(documentLocation, newDocLocation);
                        ServerDocument.RemoveCustomization(newDocLocation);
                        ServerDocument.AddCustomization(newDocLocation, assemblyLocation,
                                                        solutionID, docManifestLocationUri,
                                                        true, out string[] nonpublicCachedDataMembers);
                    }
                    else
                    {
                        LogMessage("The document could not be customized.");
                    }
                }
                catch (ArgumentException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (DocumentNotCustomizedException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (InvalidOperationException)
                {
                    LogMessage("The customization could not be removed.");
                }
                catch (IOException)
                {
                    LogMessage("The document does not exist or is read-only.");
                }
            }

            public override void Rollback(IDictionary savedState)
            {
                base.Rollback(savedState);
                DeleteDocument();
            }
            public override void Uninstall(IDictionary savedState)
            {
                base.Uninstall(savedState);
                DeleteDocument();
            }
            private void DeleteDocument()
            {
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;

                try
                {
                    File.Delete(Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation)));
                }
                catch (Exception)
                {
                    LogMessage("The document doesn't exist or is read-only.");
                }
            }
            private void LogMessage(string Message)
            {
                if (Context.Parameters.ContainsKey("LogFile"))
                {
                    Context.LogMessage(Message);
                }
            }

            static void Main() { }
            }
    }
```

Pour ajouter la personnalisation au document, vous devez disposer de l’ID de solution de votre solution au niveau du document VSTO. Cette valeur est récupérée à partir du fichier de projet Visual Studio.

Pour récupérer l’ID de solution

1. Dans le menu **générer** , cliquez sur **générer la solution** pour générer la solution au niveau du document et ajouter la propriété ID de solution au fichier projet.
2. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le projet au niveau du document **ExcelWorkbookProject**
3. Cliquez sur **UnloadProject** pour accéder au fichier projet à partir de Visual Studio.

    ![Capture d’écran de la solution de déchargement de document Excel Explorateur de solutions](media/setup-project-figure-16.jpg)

    **Figure 13 : déchargement de la solution de document Excel**

4. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur **ExcelWorkbookProject** , puis cliquez sur **EditExcelWorkbookProject. vbproj** ou **Modifiez ExcelWorkbookProject. csproj**.
5. Dans l’éditeur **ExcelWorkbookProject** , localisez l’élément **SolutionId** à l’intérieur de l’élément **PropertyGroup** .
6. Copiez la valeur GUID de cet élément.

    ![Récupération de SolutionID](media/setup-project-figure-17.jpg)

    **Figure 14 : récupération de SolutionID**

7. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur **ExcelWorkbookProject** , puis cliquez sur **recharger le projet**.
8. Cliquez sur **Oui** dans la boîte de dialogue qui s’affiche pour fermer l’éditeur **ExcelWorkbookProject** .
9. L' **ID de solution** sera utilisé dans l’action personnalisée d’installation.

La dernière étape consiste à configurer l’action personnalisée pour les étapes d' **installation** et de **désinstallation** .

### <a name="to-configure-the-setup-project"></a>Pour configurer le projet d’installation

1. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur **ExcelWorkbookSetup**, développez **Ajouter** , puis cliquez sur **sortie du projet**.
2. Dans la boîte de dialogue **Ajouter un groupe de sorties de projet** , dans la liste **projet** , cliquez sur **AddCustomizationCustomAction**.
3. Sélectionnez **sortie principale** , puis cliquez sur **OK** pour fermer la boîte de dialogue et ajouter l’assembly contenant l’action personnalisée au projet d’installation.

    ![Capture d’écran de la fenêtre action personnalisée de manifeste de document-ajouter un groupe de sorties de projet](media/setup-project-figure-18.jpg)

    **Figure 15 : action personnalisée du manifeste de document-ajouter un groupe de sorties de projet**

4. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur **ExcelWorkbookSetup**.
5. Développez **affichage** , puis cliquez sur **actions personnalisées**.
6. Dans l’éditeur d' **actions personnalisées (ExcelWorkbookSetup)** , cliquez avec le bouton droit sur **actions personnalisées** , puis cliquez sur **Ajouter une action personnalisée**.
7. Dans la boîte de dialogue **Sélectionner un élément dans le projet** , dans la liste **regarder dans** , cliquez sur dossier de l' **application**. Sélectionnez **sortie principale de AddCustomizationCustomAction (actif)** , puis cliquez sur **OK** pour ajouter l’action personnalisée à l’étape d’installation.
8. Sous le **nœud Installer**, cliquez avec le bouton droit sur **sortie principale de AddCustomizationCustomAction (actif)**, puis cliquez sur **Renommer**. Nommez l’action personnalisée **copier le document dans mes documents et attacher la personnalisation**.
9. Sous le **nœud désinstaller**, cliquez avec le bouton droit sur **sortie principale de AddCustomizationCustomAction (active)** , puis cliquez sur **Renommer**. Nommez l’action personnalisée **supprimer le document dans le dossier Documents**.

    ![Capture d’écran de la fenêtre actions personnalisées du manifeste de document](media/setup-project-figure-19.jpg)

    **Figure 16 : actions personnalisées du manifeste de document**

10. Dans l’éditeur d' **actions personnalisées (ExcelWorkbookSetup)** , cliquez avec le bouton droit sur **copier le document dans mes documents et attachez la personnalisation** , puis cliquez sur **fenêtre Propriétés**.
11. Dans la fenêtre **Propriétés** de **CustomActionData** , entrez l’emplacement de la dll de personnalisation, le manifeste de déploiement et l’emplacement du document Microsoft Office. SolutionID est également nécessaire.
12. Si vous souhaitez consigner les erreurs d’installation dans un fichier, incluez un paramètre LogFile.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Capture d’écran de l’action personnalisée pour copier le document dans mes documents Fenêtre Propriétés](media/setup-project-figure-20.jpg)

    **Figure 17 : action personnalisée pour copier le document dans mes documents**

13. L’action personnalisée pour la désinstallation requiert le nom du document, vous pouvez la fournir en utilisant le même paramètre documentLocation dans le paramètre **CustomActionData**

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Compilez et déployez le projet **ExcelWorkbookSetup** .
15. Recherchez dans le dossier **Mes documents** , puis ouvrez le fichier ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Ressources supplémentaires

[Comment : installer le Visual Studio Tools pour Office Runtime](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[assemblys PIA (Primary Interop Assembly) Office](office-primary-interop-assemblies.md)

[Entrées de Registre pour les compléments VSTO](registry-entries-for-vsto-add-ins.md)

[Custom Document Properties Overview](custom-document-properties-overview.md)

[Spécification de zones de formulaire dans le Registre Windows](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Granting Trust to Documents](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>À propos des auteurs

Wouter van Vugt est MVP Microsoft avec les technologies Office Open XML et un consultant indépendant se focalisant sur la création d’Office Business Applications (OBA) avec SharePoint, Microsoft Office et les technologies .NET associées.
Wouter est un contributeur fréquent aux sites de la communauté des développeurs, tels que [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12)). Il a publié plusieurs livres blancs et articles, ainsi qu’un livre disponible sur la ligne intitulée Open XML : a expliqué un livre électronique.
Wouter est le fondateur de code-juriste, une entreprise néerlandaise se focalisant sur la diffusion de contenu technique de pointe à travers divers canaux. Pour en savoir plus sur Wouter, consultez son blog.

Ted Pattison est MVP SharePoint, auteur, formateur et fondateur de Ted Pattison Group. En automne 2005, Ted a été embauché par le groupe Evangelism Developer Platform de Microsoft pour créer le programme de formation pour développeurs Ascend pour Windows SharePoint Services 3,0 et Microsoft Office SharePoint Server 2007. Depuis ce moment, Ted s’est entièrement concentré sur la formation des développeurs professionnels sur les technologies SharePoint 2007. Ted a fini d’écrire un livre pour Microsoft Press intitulé dans Windows SharePoint Services 3,0 qui se concentre sur l’utilisation de SharePoint comme plate-forme de développement pour la création de solutions d’entreprise. Ted écrit également une chronique axée sur les développeurs pour MSDN Magazine intitulé espace de bureau.
