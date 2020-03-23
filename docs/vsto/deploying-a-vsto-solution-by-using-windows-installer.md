---
title: Déploiement d’un studio visuel pour la solution Office à l’aide de Windows Install
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
ms.openlocfilehash: 876781cb6967f5d10dddccd54a46e218170445ab
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432363"
---
# <a name="deploying-a-visual-studio-tools-for-office-solution-using-windows-installer"></a>Déploiement d’un studio visuel pour la solution Office à l’aide de Windows Install

## <a name="summary"></a>Résumé

Découvrez comment déployer une solution Microsoft Visual Studio Tools for Office (VSTO) ou de niveau document à l’aide d’un projet d’installateur de studio visuel.

Wouter van Vugt, Avocat de code

Ted Pattison, Groupe Ted Pattison

Cet article a été mis à jour par Microsoft avec la permission des auteurs originaux.

**S’applique à :** Visual Studio Tools for Office, Microsoft Office, Microsoft Visual Studio.

## <a name="overview"></a>Vue d’ensemble

Vous pouvez développer une solution VSTO et déployer la solution à l’aide d’un package Windows Installer. Cette discussion comprend des étapes pour le déploiement d’un simple add-in Office.

## <a name="deployment-methods"></a>Méthodes de déploiement

ClickOnce peut facilement être utilisé pour créer des configurations pour vos Add-ins et solutions. Cependant, il ne peut pas installer des add-ins qui nécessitent des privilèges administratifs tels que le niveau de la machine Add-ins.

Les ajouts qui nécessitent des privilèges administratifs peuvent être installés en utilisant Windows Installer, mais il nécessite plus d’efforts pour créer la configuration.

Pour un aperçu de la façon de déployer une solution VSTO à l’aide de ClickOnce, consultez [la solution Deploy an Office en utilisant ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Déploiement de solutions Office qui ciblent le temps d’exécution VSTO

Les forfaits ClickOnce et Windows Installer doivent effectuer les mêmes tâches rudimentaires lors de l’installation d’une solution Office.

1. Installez des composants préalables sur l’ordinateur de l’utilisateur.
2. Déployez les composants spécifiques de la solution.
3. Pour les ajouts, créez des entrées de registre.
4. Faites confiance à la solution pour lui permettre d’exécuter.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Composants préalables requis sur l’ordinateur cible

Voici la liste des logiciels qui doivent être installés sur l’ordinateur pour exécuter des solutions VSTO :

- Microsoft Office 2010 ou plus récent.
- Le cadre Microsoft .NET 4 ou plus récent.
- Microsoft Visual Studio 2010 Tools pour Office Runtime.
  Le temps d’exécution offre un environnement qui gère les add-ins et les solutions de niveau document. Une version de la Runtime ne navire avec Microsoft Office, mais vous pouvez redistribuer une version spécifique avec votre add-in.
- Les assemblages Interop primaires pour Microsoft Office, si vous n’utilisez pas les types Interop Intégrés.
- Tous les assemblages d’utilitaires référencés par des projets.

### <a name="specific-components-for-the-solution"></a>Composants spécifiques pour la solution

Le paquet d’installateur doit installer ces composants sur l’ordinateur de l’utilisateur :

- Le document Microsoft Office, si vous créez une solution au niveau des documents.
- L’assemblage de personnalisation et les assemblages dont il a besoin.
- Composants supplémentaires tels que les fichiers de configuration.
- Le manifeste de l’application (.manifeste).
- Le manifeste de déploiement (.vsto).

### <a name="registry-entries-for-add-ins"></a>Inscriptions au registre des add-ins

Microsoft Office utilise les entrées de registre pour localiser et charger les add-ins. Ces entrées de registre doivent être créées dans le cadre du processus de déploiement. Pour plus d’informations sur ces inscriptions au registre, consultez [les inscriptions au Registre des modules d’add-ins VSTO](registry-entries-for-vsto-add-ins.md).

Les modules d’utilisation des perspectives qui affichent des formulaires personnalisés exigent des entrées de registre supplémentaires qui permettent d’identifier les régions de formulaire. Pour plus d’informations sur les inscriptions au registre, consultez [les inscriptions au Registre des régions du formulaire Outlook](registry-entries-for-vsto-add-ins.md#OutlookEntries).

Les solutions au niveau des documents ne nécessitent aucune inscription au registre. Au lieu de cela, les propriétés à l’intérieur du document sont utilisées pour localiser la personnalisation. Pour plus d’informations sur ces propriétés, voir [Custom Document Properties Aperçu](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Faire confiance à la solution VSTO

Pour qu’une personnalisation s’exécute, il faut faire confiance à une solution par la machine. On peut faire confiance à l’Add-in en signant le manifeste avec un certificat, en créant une relation de confiance avec une liste d’inclusion, ou en l’installant à un endroit digne de confiance sur la machine.

Pour plus d’informations sur la façon d’obtenir un certificat de signature, voir [ClickOnce Deployment et Authenticode](../deployment/clickonce-and-authenticode.md). Pour plus d’informations sur les solutions de confiance, voir [Trusting Office Solutions en utilisant les listes d’inclusion](trusting-office-solutions-by-using-inclusion-lists.md). Vous pouvez ajouter une entrée de liste d’inclusion avec une action personnalisée dans votre fichier Windows Installer. Pour plus d’informations sur l’activation de la liste d’inclusion, voir [Comment : Configurer la sécurité de la liste d’inclusion](how-to-configure-inclusion-list-security.md).

Si aucune option n’est utilisée, une invite de fiducie est affichée à l’utilisateur pour qu’il décide s’il y a à faire confiance à la solution.

Pour plus d’informations sur la sécurité liée aux solutions au niveau des documents, voir [Granting Trust to Documents](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Création d’un installateur de base

Les modèles de projet de configuration et de déploiement sont inclus dans l’extension [Microsoft Visual Studio Installer Projects](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) qui est disponible en téléchargement.

Pour créer un installateur pour une solution Office, ces tâches doivent être accomplies :

- Ajouter les éléments de la solution Office qui seront déployés.
- Pour les add-ins de niveau d’application, configurer les clés de registre.
- Configurer les composants préalables afin qu’ils puissent être installés sur les ordinateurs des utilisateurs finaux.
- Configurez les conditions de lancement pour vérifier que les composants préalables requis sont disponibles. Les conditions de lancement peuvent être utilisées pour bloquer l’installation si toutes les conditions préalables requises ne sont pas installées.

La première étape consiste à créer le projet d’installation.

### <a name="to-create-the-addin-setup-project"></a>Pour créer le projet AddIn Setup

1. Ouvrez le projet Office AddIn que vous souhaitez déployer. Pour cet exemple, nous utilisons un Add-in Excel appelé ExcelAddIn.
2. Avec le projet Office Open, sur le menu **Du fichier,** élargissez **ajouter** et cliquez sur **Nouveau Projet** pour ajouter un nouveau projet.
::: moniker range="=vs-2017"
3. Dans le dialogue **Add New Project,** étendre **d’autres types de projets** dans **le volet types de projets,** puis étendre la configuration et **le déploiement,** puis sélectionnez **Visual Studio Install**.
4. Dans le volet **Templates,** sélectionnez **Le projet d’installation** du groupe de modèles **installé visual Studio.**
::: moniker-end
::: moniker range="=vs-2019"
3. Sur le dialogue **Ajouter un nouveau projet,** sélectionnez le modèle **du projet d’installation.**
4. Cliquez sur **Suivant**.
::: moniker-end

5. Dans la boîte **nomin,** **tapez OfficeAddInSetup**.
::: moniker range="=vs-2017"
6. Cliquez **sur Open** pour créer le nouveau projet d’installation.
::: moniker-end
::: moniker range="=vs-2019"
6. Cliquez **sur Créer** pour créer le nouveau projet d’installation.
::: moniker-end

Visual Studio ouvre le File System Explorer pour le nouveau projet d’installation. Le File System Explorer vous permet d’ajouter des fichiers au projet d’installation.

   ![Capture d’écran du file d’images pour le projet d’installation](media/setup-project-figure-1.png)

   **Figure 1 : File System Explorer pour le projet d’installation**

Le projet d’installation doit déployer l’ExcelAddIn. Vous pouvez configurer le projet d’installation pour cette tâche en ajoutant la sortie du projet ExcelAddIn au projet d’installation.

### <a name="to-add-the-exceladdin-project-output"></a>Pour ajouter la sortie du projet ExcelAddIn

1. Dans la **solution Explorer**, clic droit **OfficeAddInSetup**, cliquez sur **Ajouter** puis **Project Output**.
2. Dans le dialogue **Add Project Output Group,** sélectionnez l’ExcelAddIn de la liste des projets et la production **primaire**. **ExcelAddIn**
3. Cliquez **sur OK** pour ajouter la sortie du projet au projet d’installation.

    ![Capture d’écran du projet d’installation Ajouter le dialogue project Output Group](media/setup-project-figure-2.png)

    **Figure 2 : Configuration Du projet Ajouter le dialogue du Groupe de sortie de projet**

Le projet d’installation doit déployer le manifeste de déploiement et le manifeste d’application. Ajoutez ces deux fichiers au projet d’installation en tant que fichiers autonomes du dossier de sortie du projet ExcelAddIn.

### <a name="to-add-the-deployment-and-application-manifests"></a>Pour ajouter le déploiement et les manifestes d’application

1. Dans la **solution Explorer**, clic droit **OfficeAddInSetup**, cliquez sur **Ajouter**, et cliquez sur **Fichier**.
2. Dans la boîte de dialogue **Add Files,** naviguez vers le répertoire de sortie **ExcelAddIn.** Habituellement, le répertoire de sortie est le sous-pliage de sortie de **bac\\** de l’annuaire racine de projet, selon la configuration de construction sélectionnée.
3. Sélectionnez les fichiers **ExcelAddIn.vsto** et **ExcelAddIn.dll.manifest** et cliquez sur **Open** pour ajouter ces deux fichiers au projet de configuration.

    ![Capture d’écran de l’application et le déploiement manifeste dans Solution Explorer](media/setup-project-figure-3.jpg)

    **Figure 3 : L’application et le déploiement manifestent pour l’explorateur de solution add-in**

Le référencement de l’ExcelAddIn comprend tous les composants dont ExcelAddIn a besoin. Ces composants doivent être exclus et déployés à l’aide de paquets préalables pour leur permettre d’être enregistrés correctement. En outre, les conditions de licence logicielle doivent être affichées et acceptées avant le début de l’installation.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>Exclure les dépendances du projet ExcelAddIn

1. Dans le **Solution Explorer**, dans le nœud **OfficeAddInSetup,** sélectionnez tous les éléments de dépendance sous **l’élément de dépendance détecté,** sauf pour **Microsoft .NET Framework** ou tout assemblage qui se termine par ** \*. Utilities.dll**. Les assemblages Utilities sont destinés à être déployés avec votre application.
2. Cliquez à droite sur le groupe et sélectionnez **propriétés**.
3. Dans la fenêtre **Propriétés,** changez la propriété **Exclude** à **True** pour exclure les assemblages dépendants du projet d’installation. Assurez-vous de ne pas exclure les assemblages de services publics.

    ![Capture d’écran de Solution Explorer montrant les dépendances à exclure](media/setup-project-figure-4.jpg)

    **Figure 4 : À l’exclusion des dépendances**

Vous pouvez configurer votre paquet d’installateur Windows pour installer des composants préalables en ajoutant un programme d’installation, également connu sous le nom de bootstrapper. Ce programme d’installation peut installer les composants préalables, un processus appelé bootstrapping.

Pour **l’ExcelAddIn**, ces conditions préalables doivent être installées avant que l’Add-in puisse fonctionner correctement :

- La version cadre Microsoft .NET que la solution Office cible.
- Microsoft Visual Studio 2010 Tools pour Office Runtime.

Configurer les composants dépendants comme conditions préalables

1. Dans la **solution Explorer**, cliquez à droite sur le projet **OfficeAddInSetup** et sélectionnez **propriétés**.
2. La boîte de dialogue **OfficeAddInSetup Property Pages** apparaît.
3. Cliquez sur le bouton **Préalables.**
4. Dans la boîte de dialogue De Prerequisites, sélectionnez la version correcte du cadre .NET et des outils Microsoft Visual Studio pour Office Runtime.

    ![Capture d’écran de la boîte de dialogue De Prerequisites](media/setup-project-figure-5.png)

    **Figure 5 : Boîte de dialogue préalables**

    > [!NOTE]
    >Certains des paquets préalables configurés de votre visual Studio Setup Project dépendent de la configuration de construction sélectionnée. Vous devez sélectionner les bons composants préalables pour chaque configuration de construction que vous utilisez.

Microsoft Office localise les add-ins en utilisant des clés de registre. Les clés de\_la\_ruche HKEY CURRENT USER sont utilisées pour enregistrer l’add-in pour chaque utilisateur individuel. Les clés sous\_la\_ruche HKEY LOCAL MACHINE sont utilisées pour enregistrer l’add-in pour tous les utilisateurs de la machine. Pour plus d’informations sur les clés du registre, voir [les entrées du Registre pour les add-ins VSTO](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Configurer le registre

1. Dans la **solution Explorer**, clic droit **OfficeAddInSetup**.
2. Élargir **la vue**.
3. Cliquez sur **Registre** pour ouvrir la fenêtre de l’éditeur du registre.
4. Dans le **registre (OfficeAddInSetup)** éditeur, développer **HKEY\_LOCAL\_MACHINE,** puis **Software**.
5. Supprimer ** \[la\]** clé du fabricant que l’on trouve dans **le logiciel HKEY\_LOCAL\_MACHINE\\**.
6. Élargissez **HKEY\_CURRENT\_USER,** puis **Software**.
7. Supprimer la clé ** \[du fabricant\] ** trouvée dans **le\_\_\\logiciel UTILISATEUR HKEY CURRENT**.
8. Pour ajouter des clés de registre pour l’installation add-in à droite cliquez sur la clé **Ruche utilisateur/Machine,** sélectionnez **Nouvelle Clé**. Utilisez le **logiciel de** texte pour le nom de la nouvelle clé. Cliquez à droite sur la nouvelle clé **logicielle** et créez une nouvelle clé avec le texte **Microsoft**.
9. Utilisez un processus similaire pour créer l’ensemble de la hiérarchie clé requise pour l’enregistrement add-in:

    **Utilisateur/Machine\\Hive\\\\Software\\\\Microsoft\\Office Excel Addins SampleCompany.ExcelAddIn**

    Le nom de la société est souvent utilisé comme préfixe pour le nom de l’add-in pour fournir un caractère unique.

10. Cliquez à droite sur la touche **SampleCompany.ExcelAddIn,** sélectionnez **Nouvelle,** et cliquez sur **la valeur de la chaîne**. Utilisez le texte **Description** pour le nom.
11. Utilisez cette étape pour ajouter trois autres valeurs :
    - **FriendlyName** de type **String**
    - **LoadBehavior** de type **DWORD**
    - **Manifeste** de la **chaîne de** type

12. Cliquez à droite sur la valeur **description** dans l’éditeur du registre et cliquez sur **Properties Window**. Dans la **fenêtre propriétés**, entrez **Excel Demo AddIn** pour la propriété Value.
13. Sélectionnez la clé **FriendlyName** dans l’éditeur du registre. Dans la **fenêtre propriétés**, changer la propriété **De la valeur** à Excel **Demo AddIn**.
14. Sélectionnez la clé **LoadBehavior** dans l’éditeur du registre. Dans la **fenêtre des propriétés**, changer la propriété **de valeur** à **3.** La valeur 3 pour le LoadBehavior indique que l’add-in doit être chargé au démarrage de l’application hôte. Pour plus d’informations sur le comportement de chargement, voir [les entrées du Registre pour VSTO Add-ins](registry-entries-for-vsto-add-ins.md).

15. Sélectionnez la clé **Manifeste** dans l’éditeur du registre. Dans la **fenêtre propriétés**, modifier la propriété **De valeur** pour **déposer:///[TARGETDIR]ExcelAddIn.vsto-vstolocal**

    ![Capture d’écran de l’éditeur du registre](media/setup-project-figure-6.png)

    **Figure 6 : Mise en place des clés du registre**

      Le temps d’exécution VSTO utilise cette clé de registre pour localiser le manifeste de déploiement. La macro [TARGETDIR] sera remplacée par le dossier où l’add-in est installé. La macro inclura le caractère de fuite, de sorte que le nom de fichier du manifeste de déploiement devrait être ExcelAddIn.vsto sans le caractère.
      Le **postfix vstolocal,** indique à l’exécution VSTO que l’Add-in devrait charger à partir de cet emplacement au lieu du cache ClickOnce. La suppression de ce correctif postier entraînera la copie de la personnalisation dans le cache ClickOnce.

   >[!WARNING]
   >Vous devriez être très prudent avec l’éditeur de registre dans Visual Studio. Par exemple, si vous définissez accidentellement DeleteAtUninstall pour la mauvaise clé, vous pouvez supprimer une partie active du registre, laissant l’ordinateur utilisateur dans un état incohérent, voire pire, cassé.

Les versions 64 bits de Office utiliseront la ruche de registre 64 bits pour rechercher des add-ins. Pour enregistrer les add-ins sous la ruche de registre 64 bits, la plate-forme cible du projet d’installation doit être réglée à 64 bits seulement.

1. Sélectionnez le projet **OfficeAddInSetup** dans l’explorateur de solutions.
2. Aller à la fenêtre **Propriétés** et définir la propriété **TargetPlatform** à **x64**.

L’installation d’un Add-in pour les versions 32 et 64 bits de Office, vous obligera à créer deux paquets MSI distincts. Un pour 32 bits et un pour 64 bits.

  ![Capture d’écran de la fenêtre propriétés montrant la plate-forme cible pour l’enregistrement des add-ins avec Office 64 bits](media/setup-project-figure-7.jpg)

  **Figure 7 : Plate-forme cible pour l’enregistrement des modules avec bureau 64 bits**

Si le paquet MSI est utilisé pour installer l’Add-in ou la solution, il peut être installé sans que les conditions préalables requises soient installées. Vous pouvez utiliser les conditions de lancement dans le MSI pour empêcher l’Add-in d’installer si les conditions préalables ne sont pas installées.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Configurer une condition de lancement pour détecter le RUNtime VSTO

1. Dans la **solution Explorer**, clic droit **OfficeAddInSetup**.
2. Élargir **la vue**.
3. Cliquez sur **conditions de lancement**.
4. Dans l’éditeur **Conditions de lancement (OfficeAddInSetup),** en clic **droit, exigences en**clics sur target Machine, puis cliquez sur **Add Registry Launch Condition**. Cette condition de recherche peut rechercher dans le registre une clé que le temps d’exécution VSTO installe. La valeur de la clé est alors disponible pour les différents morceaux de l’installateur à travers une propriété nommée. L’état de lancement utilise la propriété définie par l’état de recherche pour vérifier une certaine valeur.
5. Dans l’éditeur **Conditions de lancement (OfficeAddInSetup),** sélectionnez **l’état de recherche d’RegistryEntry1,** cliquez à droite sur l’état et sélectionnez **La fenêtre propriétés.**

6. Dans la fenêtre **Propriétés** , définissez les propriétés suivantes :
   1. Définissez la valeur de **(Nom)** à **la recherche de VSTO 2010 Runtime**.
   2. Changer la valeur de la **propriété** en **VSTORUNTIMEREDIST**.
   3. Définissez la valeur de **RegKey** à **SOFTWARE\\Microsoft\\VSTO Runtime Setup\\v4R**
   4. Laissez la propriété **Root** réglée à **vsdrrHKLM**.
   5. Modifier la propriété **de valeur** en **Version**.

7. Dans l’éditeur **Conditions de lancement (OfficeAddInSetup),** sélectionnez **l’état** de lancement conditionnel1, cliquez à droite sur l’état et sélectionnez **Properties Window**.
8. Dans la fenêtre Propriétés, définissez les propriétés suivantes :
   1. Définissez le **(Nom)** pour **vérifier la disponibilité de VSTO 2010 Runtime**.
   2. Changer la valeur de la **condition** en **VSTORUNTIMEREDIST\>-"10.0.30319"**
   3. Laissez la propriété **InstallURL** vide.
   4. Définir le **message** sur **the Visual Studio 2010 Tools for Office Runtime n’est pas installé. S’il vous plaît exécuter Setup.exe pour installer l’Add-in**.

        ![Capture d’écran de la fenêtre propriétés pour l’état de lancement de la disponibilité de Runtime Verify](media/setup-project-figure-8.jpg)

        **Figure 8 : Fenêtre des propriétés pour l’état de lancement de la disponibilité de l’exécution de vérification**

 L’état de lancement ci-dessus vérifie explicitement la présence du temps d’exécution VSTO lorsqu’il est installé par le paquet bootstrapper.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Configurer une condition de lancement pour détecter le runtime VSTO installé par Office

1. Dans l’éditeur **Conditions de lancement (OfficeAddInSetup),** cliquez à droite **sur Search Target Machine,** puis cliquez sur **Ajouter la recherche de registre**.
2. Sélectionnez **l’état de recherche De RegistryEntry1,** cliquez à droite sur l’état et sélectionnez **la fenêtre propriétés**.
3. Dans la fenêtre **Propriétés** , définissez les propriétés suivantes :
    1. Définissez la valeur de **(Nom)** à **la recherche d’Office VSTO Runtime**.
    2. Changer la valeur de **la propriété** à **OfficeRuntime**.
    3. Définissez la valeur de **RegKey** à **SOFTWARE\\Microsoft\\VSTO Runtime Setup\\v4**.
    4. Laissez la propriété **Root** réglée à **vsdrrHKLM**.
    5. Modifier la propriété **de valeur** en **Version**.

4. Dans l’éditeur **Conditions de lancement (OfficeAddInSetup),** sélectionnez **l’état de lancement de disponibilité De 2010 De Verify VSTO 2010** défini plus tôt, cliquez à droite sur l’état et sélectionnez **La fenêtre de propriétés.**

5. Changer la valeur de la propriété **Condition** à **VSTORUNTIMEREDIST \>-"10.0.30319" OU OFFICERUNTIME\>'"10.0.21022"**. Les numéros de version peut-être différents pour vous en fonction des versions de l’exécution que votre Add-in nécessite.

    ![Capture d’écran du Windows Propriétés pour l’état de lancement](media/setup-project-figure-9.jpg)
  
    **Figure 9 : Propriétés Windows pour la disponibilité de Temps d’exécution de vérification par l’état de lancement de Redist ou de Bureau**

Si un Add-in cible .NET Framework 4, ou plus récent, les types à l’intérieur des Assemblées interop primaires (PIA), qui sont référencés, peuvent être intégrés dans l’assemblage VSTO.

Pour vérifier si les types Interop seront intégrés dans votre Add-in en effectuant les étapes suivantes :

1. Élargir le nœud de référence dans Solution Explorer
2. Sélectionnez l’une des références de l’ÉFVP, par **exemple, Office**.
3. Affichez les fenêtres des propriétés en frappant F4 ou en sélectionnant les propriétés du menu contexte des Assemblées.
4. Vérifiez la valeur de la propriété **Embed Interop Types**.

Si la valeur est définie à **True**, alors les types sont intégrés et vous pouvez sauter vers le bas pour construire la section [**du projet d’installation.**](#to-build-the-setup-project)

Pour plus d’informations, voir [Type Equivalence et Embedded Interop Types](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Configurer les conditions de lancement pour détecter que pour les AIP Office

1. Dans l’éditeur **Conditions de lancement (OfficeAddInSetup),** en clic **droit, exigences en**clics sur Target Machine, puis **cliquez sur Add Windows Installer Launch Condition**. Cette condition de lancement recherche une PIA Office en recherchant l’ID composant spécifique.
2. Cliquez à droite **Recherche de composant1** et cliquez sur **Properties Window** pour afficher les propriétés de l’état de lancement.
3. Dans la **fenêtre propriétés**, définissez ces propriétés :

    1. Modifier la valeur de la propriété **(Nom)** à **Search for Office Shared PIA**
    2. Modifiez la valeur de **l’ID composant** en composant pour le composant Office que vous utilisez. Vous pouvez trouver la liste des ids composant dans le tableau ci-dessous, par exemple **'64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4'.**
    3. Modifier la valeur de la propriété **à** **HASSHAREDPIA**.

4. Dans l’éditeur **Conditions de lancement (OfficeAddInSetup),** cliquez à droite **Condition1** et cliquez sur **Properties Window** pour afficher les propriétés de l’état de lancement.

5. Modifier ces propriétés de **Condition1**:

    1. Modifier le **(Nom)** pour vérifier la **disponibilité de l’ÉFVP partagée**par bureau .
    2. Modifier la **condition** en **HASSHAREDPIA**.
    3. Laisser **InstallUrl** vide.
    4. Modifier le **message** en **un composant requis pour interagir avec Excel n’est pas disponible. S’il vous plaît exécuter setup.exe**.

    ![Capture d’écran de la fenêtre propriétés pour l’état de lancement de l’AIP partagé de Bureau de vérification](media/setup-project-figure-10.jpg)
  
    **Figure 10 : Fenêtre des propriétés pour l’état de lancement de l’ÉFVP partagé par Le Bureau de vérification**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>Composants des assemblées Interop primaires pour Microsoft Office

|Assemblage principal d’interop|Office 2010|Office 2013|Office 2013 (64 bits)|Office 2016|Office 2016 (64 bits)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|EA7564AC-C67D-4868-BE5C-26E4FC2223FF|C8A65ABE-3270-4FD7-B854-50C8082C8F39|E3BD1151-B9CA-4D45-A77E-51A6E0ED322A|C4ace6DB-AA99-401F-8BE6-8784BD09F003|C4ace6DB-AA99-401F-8BE6-8784BD09F003|
|InfoPath|4153F732-D670-4E44-8AB7-500F2B576BDA|0F825A16-25B2-4771-A497-FC8AF3B355D8|C5BBD36E-B320-47EF-A512-556B99CB7E41|-|-|
|Outlook|1D844339-3DAE-413E-BC13-62D6A52816B2|F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136|7824A03F-28CC-4371-BC54-93D15EFC1E7F|7C6D92EF-7B45-46E5-8670-819663220E4E|7C6D92EF-7B45-46E5-8670-819663220E4E|
|PowerPoint|EECBA6B8-3A62-44AD-99EB-8666265466F9|813139AD-6DAB-4DDD-8C6D-0CA30D073B41|05758318-BCFD-4288-AD8D-81185841C235|E0A76492-0FD5-4EC2-8570-AE1BAA61DC88|E0A76492-0FD5-4EC2-8570-AE1BAA61DC88|
|Visio|3EA123B5-6316-452E-9D51-A489E06E2347|C1713368-12A8-41F1-ACA1-934B01AD6EEB|2CC0B221-22D2-4C15-A9FB-DE818E51AF75|2D4540EC-2C88-4C28-AE88-2614B5460648|2D4540EC-2C88-4C28-AE88-2614B5460648|
|Word|8B74A499-37F8-4DEA-B5A0-D72FC501CEFA|9FE736B7-B1EE-410C-8D07-082891C3DAC8|13C07AF5-B206-4A48-BB5B-B8022333E3CA|-DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161|-DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161|
|Microsoft Forms 2.0|B2279272-3FD2-434D-B94E-E4E0F8561AC4|B2279272-3FD2-434D-B94E-E4E0F8561AC4|A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC|-|-|
|Microsoft Graph|011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E|52DA4B37-B8EB-4B7F-89C1-824654CE4C70|24706F33-F0CE-4EB4-BC91-9E935394F510|-|-|
|Balise active|7102C98C-EF47-4F04-A227-FE33650BF954|487A7921-EB3A-4262-BB5B-A5736B732486|74EFC1F9-747D-4867-B951-EFCF29F51af7|-|-|
|Bureau partagé|64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4|6A174BDB-0049-4D1C-86EF-3114CB0C4C4E|76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05|625F5772-C1B3-497E-8ABE-7254EDB00506|625F5772-C1B3-497E-8ABE-7254EDB00506|
|Projet|957A4EC0-E67B-4E86-A383-6AF7270B216A|1C50E422-24FA-44A9-A120-E88280C8C341|706D7F44-8231-489D-9B25-3025ADE9F114|107BCD9A-F1DC-4004-A444-33706FC10058|107BCD9A-F1DC-4004-A444-33706FC10058|

  ![Capture d’écran des conditions de lancement final](media/setup-project-figure-11.jpg)

  **Figure 11 : Conditions de lancement fin**

Vous pouvez affiner les conditions de lancement de l’installation ExcelAddIn. Par exemple, il peut être utile de vérifier si l’application cible réelle Office est installée.

### <a name="to-build-the-setup-project"></a>Pour construire le projet d’installation

1. Dans la **solution Explorer**, cliquez à droite sur le projet **OfficeAddInSetup** et cliquez sur **Build**.
2. En utilisant **Windows Explorer**, naviguer vers l’annuaire de sortie du projet **OfficeAddInSetup** et aller au dossier Release ou Debug, en fonction de la configuration de construction sélectionnée. Copiez tous les fichiers du dossier à un endroit où les utilisateurs peuvent accéder.

Pour tester la configuration ExcelAddIn

1. Naviguez jusqu’à l’endroit où vous avez copié **OfficeAddInSetup.**
2. Double-clic sur le fichier setup.exe pour installer **l’Add-in OfficeAddInSetup.** Acceptez toutes les conditions de licence logicielle qui apparaissent, et complétez l’assistant de configuration pour installer l’add-in sur l’ordinateur utilisateur.

La solution Excel Office doit installer et exécuter à partir de l’emplacement spécifié pendant la configuration.

## <a name="additional-requirements-for-document-level-solutions"></a>Exigences supplémentaires pour les solutions au niveau des documents

Le déploiement de solutions au niveau des documents nécessite quelques étapes de configuration différentes dans le projet de configuration De Windows Installer.

Voici une liste des étapes de base nécessaires au déploiement d’une solution au niveau des documents :

- Créez le visual Studio Setup Project.
- Ajoutez la sortie principale de votre solution au niveau des documents. La sortie principale comprend également le document Microsoft Office.
- Ajoutez le déploiement et l’application se manifeste comme des fichiers en vrac.
- Exclure les composants dépendants de l’emballage de l’installateur (à l’exception des assemblages d’utilitaires).
- Configurer les paquets préalables.
- Configurer les conditions de lancement.
- Construisez le projet d’installation et copiez les résultats sur le lieu du déploiement.
- Déployez la solution au niveau du document sur l’ordinateur utilisateur en exécutant la configuration.
- Mettre à jour les propriétés de documents personnalisées si nécessaire.

### <a name="changing-the-location-of-the-deployed-document"></a>Modification de l’emplacement du document déployé

Les propriétés à l’intérieur d’un document Office sont utilisées pour localiser les solutions de niveau de document. Si le document est installé dans le même dossier que l’assemblage VSTO, aucune modification n’est requise. Toutefois, s’il est installé dans différents dossiers, ces propriétés devront être mises à jour pendant la configuration.

Pour plus d’informations sur ces propriétés de documents, voir [Custom Document Properties Aperçu](custom-document-properties-overview.md).

Pour modifier ces propriétés, vous devez utiliser une action personnalisée pendant la configuration.

L’exemple suivant utilise une solution au niveau des documents appelée ExcelWorkbookProject et un projet de configuration appelé ExcelWorkbookSetup. Le projet ExcelWorkbookSetup est configuré en utilisant les mêmes étapes décrites ci-dessus, à l’exception de la fixation des clés du registre.

Pour ajouter le projet d’action personnalisé à votre solution Visual Studio

1. Ajoutez un nouveau projet .NET Console à la solution en cliquant à droite sur le **projet de déploiement de documents office** dans la solution **Explorer**
2. Élargissez **ajouter** et cliquez sur **new Project**.
3. Sélectionnez le modèle d’application console et nommez le projet **AddCustomizationCustomAction**.

    ![Capture d’écran de l’explorateur de solution - AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Figure 12: Solution Explorer - AddCustomizationCustomAction**

4. Ajouter une référence à ces assemblages :
    1. System.ComponentModel
    2. System.Configuration.Install
    3. Microsoft.VisualStudio.Tools.Applications (en anglais seulement)
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. Copiez ce code en Program.cs ou Program.vb

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

Pour ajouter la personnalisation au document, vous devez avoir l’ID de solution de votre solution de niveau de document VSTO. Cette valeur est récupérée dans le fichier du projet Visual Studio.

Pour récupérer l’ID de la solution

1. Sur le menu **Build,** cliquez sur **Build Solution** pour construire la solution au niveau du document et ajouter la propriété ID de solution au fichier du projet.
2. Dans la **Solution Explorer**, cliquez à droite sur le projet de niveau document **ExcelWorkbookProject**
3. Cliquez **sur UnloadProject** pour accéder au fichier du projet depuis Visual Studio.

    ![Capture d’écran de Solution Explorer déchargeant Excel Document Solution](media/setup-project-figure-16.jpg)

    **Figure 13 : Déchargement de la solution de document Excel**

4. Dans la **Solution Explorer**, cliquez à droite **ExcelWorkbookProject** et cliquez sur **EditExcelWorkbookProject.vbproj** ou **Modifier ExcelWorkbookProject.csproj**.
5. Dans l’éditeur **ExcelWorkbookProject,** localisez l’élément **SolutionID** à l’intérieur de l’élément **PropertyGroup.**
6. Copiez la valeur GUID de cet élément.

    ![Récupération de la SolutionID](media/setup-project-figure-17.jpg)

    **Figure 14 : Récupération de la SolutionID**

7. Dans la **Solution Explorer**, cliquez à droite **ExcelWorkbookProject** et cliquez sur **Reload Project**.
8. Cliquez **oui** dans la boîte de dialogue qui semble fermer l’éditeur **ExcelWorkbookProject.**
9. **L’ID Solution** sera utilisé dans l’action personnalisée Installation.

La dernière étape consiste à configurer l’action personnalisée pour les étapes **Installer** et **Désinstaller.**

### <a name="to-configure-the-setup-project"></a>Configurer le projet d’installation

1. Dans la **solution Explorer**, clic droit **ExcelWorkbookSetup**, **expandz Ajouter** et cliquez sur Production du **projet**.
2. Dans la boîte de dialogue **Add Project Output Group,** dans la liste **de projet,** cliquez sur **AddCustomizationCustomAction**.
3. Sélectionnez **La sortie primaire** et cliquez sur **OK** pour fermer la boîte de dialogue et ajouter l’assemblage contenant l’action personnalisée au projet d’installation.

    ![Capture d’écran de l’action personnalisée De manifeste de document - Ajouter la fenêtre du groupe de sortie de projet](media/setup-project-figure-18.jpg)

    **Figure 15 : Document Manifest Custom Action - Ajouter Project Output Group**

4. Dans la **Solution Explorer**, cliquez à droite **ExcelWorkbookSetup**.
5. Élargissez **la vue** et cliquez sur **Custom Actions**.
6. Dans l’éditeur **Custom Actions (ExcelWorkbookSetup),** cliquez à droite **sur Custom Actions** et cliquez sur Ajouter **l’action personnalisée**.
7. Dans la boîte de dialogue **Select Item in Project,** dans la liste **Look In,** cliquez sur **Le dossier d’application**. Sélectionnez **la sortie primaire de AddCustomizationCustomAction (active)** et cliquez sur **OK** pour ajouter l’action personnalisée à l’étape d’installation.
8. Sous le **nœud d’installation**, cliquez à droite **sortie primaire de AddCustomizationCustomAction (Active)**, et cliquez sur **Renommez**. Nommez le **document d’action personnalisée De copie à Mes Documents et attachez la personnalisation.**
9. Sous le **nœud Uninstall**, cliquez à droite **Sortie primaire de AddCustomizationCustomAction (Active)** et cliquez sur **Rename**. Nommez l’action personnalisée **Supprimer le document du dossier Documents**.

    ![Capture d’écran de la fenêtre Document Manifest Custom Actions](media/setup-project-figure-19.jpg)

    **Figure 16 : Document Manifeste Custom Actions**

10. Dans l’éditeur **Custom Actions (ExcelWorkbookSetup),** cliquez à droite **sur le document Copy sur Mes Documents et attachez la personnalisation** et cliquez sur **Properties Window**.
11. Dans la fenêtre **CustomActionData** **Properties,** entrez l’emplacement de la personnalisation DLL, le manifeste de déploiement et l’emplacement du document Microsoft Office. La SolutionID est également nécessaire.
12. Si vous souhaitez enregistrer des erreurs de configuration dans un fichier, incluez un paramètre LogFile.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Capture d’écran de l’action personnalisée pour copier le document à la fenêtre de mes propriétés de documents](media/setup-project-figure-20.jpg)

    **Figure 17 : Action personnalisée pour copier le document à mes documents**

13. L’action personnalisée pour Uninstall a besoin du nom du document, vous pouvez le fournir en utilisant le même paramètre de documentLocation dans le **CustomActionData**

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Compilez et déployez le projet **ExcelWorkbookSetup.**
15. Regardez dans mon dossier **Documents** et ouvrez le fichier ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Ressources supplémentaires

[Comment : Installer les outils visual studio pour Office Runtime](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Assemblées Interop primaires de bureau](office-primary-interop-assemblies.md)

[Inscriptions au registre des add-ins VSTO](registry-entries-for-vsto-add-ins.md)

[Custom Document Properties Overview](custom-document-properties-overview.md)

[Spécifier les régions de formulaire dans le registre Windows](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Granting Trust to Documents](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>À propos des auteurs

Wouter van Vugt est un MVP Microsoft avec des technologies Office Open XML et un consultant indépendant se concentrant sur la création d’applications d’entreprise Office (IA) avec SharePoint, Microsoft Office, et les technologies .NET connexes.
Wouter contribue fréquemment aux sites communautaires de développeurs tels que [OpenXmlDeveloper.org](http://openxmldeveloper.org/) et [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12)). Il a publié plusieurs livres blancs et articles ainsi qu’un livre disponible en ligne intitulé Open XML: Explained e-book.
Wouter est le fondateur de Code-Counsel, une société néerlandaise qui se concentre sur la fourniture de contenu technique de pointe par le biais de divers canaux. Vous pouvez en savoir plus sur Wouter en lisant son blog et en visitant le [site Web Code-Counsel](http://www.code-counsel.net/).

Ted Pattison est MVP SharePoint, auteur, formateur et fondateur de Ted Pattison Group. À l’automne 2005, Ted a été embauché par le groupe d’évangélisation de la plate-forme de développement de Microsoft pour l’auteur du programme de formation des développeurs Ascend pour Windows SharePoint Services 3.0 et Microsoft Office SharePoint Server 2007. Depuis, Ted s’est entièrement concentré sur l’éducation des développeurs professionnels sur les technologies SharePoint 2007. Ted a fini d’écrire un livre pour Microsoft Press intitulé Inside Windows SharePoint Services 3.0 qui se concentre sur la façon d’utiliser SharePoint comme une plate-forme de développement pour la construction de solutions d’affaires. Ted écrit également une chronique axée sur les développeurs pour MSDN Magazine intitulée Office Space.
