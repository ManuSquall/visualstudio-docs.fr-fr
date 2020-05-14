---
title: Déployer une solution Office en utilisant ClickOnce
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4adbd08d13d26c717beeb454bd323185bb88640
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416560"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Déployer une solution Office en utilisant ClickOnce
  Vous pouvez déployer votre solution Office plus rapidement en utilisant ClickOnce. Si vous publiez des mises à jour, votre solution les détecte et les installe automatiquement. Toutefois, avec ClickOnce, vous devez installer votre solution séparément pour chaque utilisateur d'un ordinateur. Par conséquent, vous devriez envisager d’utiliser Windows Installer (*.msi*) si plus d’un utilisateur exécutera votre solution sur le même ordinateur.

## <a name="in-this-topic"></a>Dans cette rubrique

- [Publier la solution](#Publish)

- [Déterminer comment accorder un niveau de confiance à la solution](#Trust)

- [Aider les utilisateurs à installer la solution](#Helping)

- [Placer le document d'une solution sur l'ordinateur de l'utilisateur final (personnalisations au niveau du document uniquement)](#Put)

- [Placer le document d'une solution sur un serveur exécutant SharePoint (personnalisations au niveau du document uniquement)](#SharePoint)

- [Créer un programme d’installation personnalisé](#Custom)

- [Publier une mise à jour](#Update)

- [Modifier l'emplacement d'installation d'une solution](#Location)

- [Restaurer la version antérieure d'une solution](#Roll)

  Pour plus d’informations sur la façon de déployer une solution Office en créant un fichier d’installateur Windows, consultez [la solution Deploy an Office en utilisant Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="publish-the-solution"></a><a name="Publish"></a>Publier la solution
 Vous pouvez publier votre solution en utilisant le **Assistant De publication** ou le Concepteur de **projet**. Dans cette procédure, vous utiliserez le **concepteur de projet** car il fournit l’ensemble complet des options de publication. Voir [Publish wizard &#40;Office development in Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Pour publier la solution

1. Dans **Solution Explorer**, choisissez le nœud qui porte le nom de votre projet.

2. Dans la barre de menus, choisissez **Projet**, *Propriétés de* **NomProjet**.

3. Dans le **concepteur de projet**, choisissez l’onglet **Publier,** que l’illustration suivante montre.

    ![Onglet Publier du Concepteur de projets](../vsto/media/vsto-publishtab.png "Onglet Publier du Concepteur de projets")

4. Dans la boîte **de localisation du dossier d’édition (serveur de pip, ou trajectoire** de fichier), entrez le chemin du dossier où vous souhaitez que le concepteur de **projet** copie les fichiers de solution.

    Vous pouvez entrer n'importe lequel des types de chemins d'accès suivants.

   - Un chemin local (par exemple, *C: 'FolderName’FolderName).*

   - Un chemin de la Convention de Nommage uniforme (UNC) vers un dossier sur votre réseau (par exemple, * \\'ServerName’FolderName*).

   - Un chemin relatif (par exemple, *PublishFolder\\*, qui est le dossier dans lequel le projet est publié par défaut).

5. Dans la boîte **URL Du dossier d’installation,** entrez le chemin entièrement qualifié de l’endroit où les utilisateurs finaux trouveront votre solution.

    Si vous ne connaissez pas encore l’emplacement, n’entrez rien dans ce domaine. Par défaut, ClickOnce recherche des mises à jour dans le dossier à partir duquel les utilisateurs installent la solution.

6. Choisissez le bouton **Composants requis** .

7. Dans la boîte de dialogue **De Prerequisites,** assurez-vous que le **programme d’installation Create pour installer** la case à cocher des composants préalables est sélectionné.

8. Dans le **Choisir quelles conditions préalables à installer** liste, sélectionnez les cases à cocher pour Windows Installer **4.5** et le paquet cadre .NET approprié.

    Par exemple, si votre [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]solution cible les cases à cocher pour **Windows Installer 4.5** et **Microsoft .NET Framework 4.5 Complet**.

9. Si votre solution cible le cadre .NET 4.5, sélectionnez également la boîte à cocher **Visual Studio 2010 Tools for Office Runtime.**

    > [!NOTE]
    > Par défaut, cette case à cocher n’apparaît pas. Pour afficher cette case à cocher, vous devez créer un package de programme d'amorçage. Voir [Créer un forfait Bootstrapper pour un Add-in VSTO Office 2013 avec Visual Studio 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md).

10. Sous **Spécifiez l’emplacement d’installation pour les conditions préalables,** choisissez l’une des options qui apparaissent, puis choisissez le bouton **OK.**

     Le tableau suivant décrit chaque option.

    |Option|Description|
    |------------|-----------------|
    |**Télécharger les composants requis à partir du site web du fournisseur de composants**|L'utilisateur est invité à télécharger et à installer les composants requis du fournisseur.|
    |**Télécharger les composants requis à partir de l’emplacement de mon application**|Les logiciels requis sont installés avec la solution. Si vous choisissez cette option, Visual Studio copie tous les packages de composants requis dans l'emplacement de publication à votre place. Pour que cette option fonctionne, les packages de composants requis doivent être sur l'ordinateur de développement.|
    |**Télécharger les composants requis depuis l’emplacement suivant**|Visual Studio copie tous les packages de composants requis dans l'emplacement que vous spécifiez et les installe avec la solution.|

     Voir [La boîte de dialogue de Prerequisites](../ide/reference/prerequisites-dialog-box.md).

11. Choisissez le bouton **Mises à jour,** spécifiez la fréquence à laquelle vous souhaitez l’add-in ou la personnalisation VSTO de chaque utilisateur final pour vérifier les mises à jour, puis choisissez le bouton **OK.**

    > [!NOTE]
    > Si vous déployez en utilisant un CD ou un lecteur amovible, choisissez le bouton **d’option De mise à jour Jamais vérifié.**

     Pour plus d’informations sur la façon de publier une mise à jour, voir [Publier une mise à jour](#Update).

12. Choisissez le bouton **Options,** examinez les options dans la boîte de dialogue **Options,** puis choisissez le bouton **OK.**

13. Choisissez le bouton **Publier maintenant.**

     Visual Studio ajoute les dossiers et les fichiers suivants au dossier de publication que vous avez spécifié précédemment dans cette procédure.

    - Le dossier **de fichiers d’application.**

    - Le programme d'installation.

    - Un manifeste de déploiement qui pointe vers le manifeste de déploiement de la version la plus récente.

      Le dossier **Fichiers d’application** contient un sous-pli pour chaque version que vous publiez. Chaque sous-dossier spécifique à la version contient les fichiers suivants.

    - Un manifeste d’application.

    - Un manifeste de déploiement.

    - Des assemblys de personnalisation.

      L'illustration suivante représente la structure du dossier de publication pour un complément VSTO Outlook.

      ![Publier la structure du dossier](../vsto/media/publishfolderstructure.png "Structure du dossier de publication")

    > [!NOTE]
    > ClickOnce joint l’extension *.deploy* aux assemblages afin qu’une installation sécurisée des Services d’information Internet (IIS) ne bloque pas les fichiers en raison d’une extension dangereuse. Lorsque l’utilisateur installe la solution, ClickOnce supprime l’extension *.deploy.*

14. Copiez les fichiers solution dans l'emplacement d'installation que vous avez spécifié précédemment dans cette procédure.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a>Décidez comment vous voulez accorder la confiance à la solution
 Avant qu'une solution puisse s'exécuter sur les ordinateurs des utilisateurs, vous devez soit accorder votre confiance soit les utilisateurs doivent répondre à une invite d'approbation lorsqu'ils installent la solution. Pour accorder un niveau de confiance à la solution, signez les manifestes à l'aide d'un certificat qui identifie un éditeur connu et approuvé. Voir [Trust la solution en signant l’application et le déploiement manifeste](../vsto/granting-trust-to-office-solutions.md#Signing).

 Si vous déployez une personnalisation au niveau du document et que vous souhaitez mettre le document dans un dossier sur l’ordinateur de l’utilisateur ou rendre le document disponible sur un site SharePoint, assurez-vous qu’Office fait confiance à l’emplacement du document. Voir [Grant trust to documents](../vsto/granting-trust-to-documents.md).

## <a name="help-users-install-the-solution"></a><a name="Helping"></a>Aider les utilisateurs à installer la solution
 Les utilisateurs peuvent installer la solution en exécutant le programme de configuration, en ouvrant le manifeste de déploiement, ou pendant la personnalisation au niveau du document, en ouvrant le document directement. Il est recommandé que les utilisateurs installent votre solution à l'aide du programme d'installation. Les deux autres approches ne garantissent pas l’installation du logiciel préalable. Si les utilisateurs souhaitent ouvrir le document à partir de l'emplacement d'installation, ils doivent l'ajouter à la liste des emplacements approuvés dans le Centre de gestion de la confidentialité des applications Office.

### <a name="opening-the-document-of-a-document-level-customization"></a>Ouverture du document d'une personnalisation au niveau du document
 Les utilisateurs peuvent ouvrir le document d'une personnalisation au niveau du document à partir de l'emplacement d'installation ou en copiant le document sur leur ordinateur local, puis en ouvrant la copie.

 Il est recommandé que les utilisateurs ouvrent une copie du document sur leurs ordinateurs afin que plusieurs utilisateurs n'essayent pas d'ouvrir la même copie simultanément. Pour mettre en œuvre ce principe, vous pouvez configurer votre programme d'installation pour copier le document sur les ordinateurs d'utilisateur. Voir [Mettez le document d’une solution sur l’ordinateur de l’utilisateur final (personnalisations au niveau des documents seulement)](#Put).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Installer la solution en ouvrant le manifeste de déploiement à partir d’un site Web de l’IIS
 Les utilisateurs peuvent installer une solution Office en ouvrant le manifeste de déploiement à partir du Web. Toutefois, une installation sécurisée des Services d’information Internet (IIS) bloquera les fichiers qui ont l’extension *.vsto.* Le type MIME doit être défini dans IIS avant de pouvoir déployer une solution Office à l'aide d'IIS.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Pour ajouter le type MIME .vsto à IIS 6.0

1. Sur le serveur qui fonctionne IIS 6.0, choisissez **Start** > **All Programs** > **Administrative Tools** >  **Internet Information Services (IIS) Manager**.

2. Choisissez le nom de l’ordinateur, le dossier **Web Des sites** ou le site Web que vous configurez.

3. Sur la barre de menu, choisissez **Action** > **Properties**.

4. Sur l’onglet **HTTP Headers,** choisissez le bouton **MIME Types.**

5. Dans la fenêtre **MIME Types,** choisissez le **nouveau** bouton.

6. Dans la fenêtre **miME Type,** entrez **.vsto** comme extension, entrez **l’application/x-ms-vsto** comme type MIME, puis appliquez les nouveaux paramètres.

    > [!NOTE]
    > Pour que les modifications soient prises en compte, vous devez redémarrer le service de publication World Wide Web ou attendre le recyclage du processus de travail. Vous devez ensuite rincer le cache de disque du navigateur, puis essayer d’ouvrir le fichier *.vsto* à nouveau.

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Pour ajouter le type MIME .vsto à IIS 7,0

1. Sur le serveur qui fonctionne IIS 7.0, choisissez **Start** > **All Programs** > **Accessoires**.

2. Ouvrez le menu raccourci pour **Command Prompt,** puis choisissez **Run comme administrateur.**

3. Dans la boîte **ouverte,** entrez dans le chemin suivant, puis choisissez le bouton **OK.**

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Entrez la commande suivante, puis appliquez les nouveaux paramètres.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Pour que les modifications soient prises en compte, vous devez redémarrer le service de publication World Wide Web ou attendre le recyclage du processus de travail. Vous devez ensuite rincer le cache de disque du navigateur, puis essayer d’ouvrir le fichier *.vsto* à nouveau.

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a>Mettez le document d’une solution sur l’ordinateur de l’utilisateur final (personnalisations au niveau des documents seulement)
 Vous pouvez copier le document de votre solution sur l’ordinateur de l’utilisateur final en créant une action post-déploiement. De cette façon, l’utilisateur n’a pas à copier manuellement le document de l’emplacement de l’installation à son ordinateur après avoir installé votre solution. Vous devrez créer une classe qui définit l’action post-déploiement, construire et publier la solution, modifier le manifeste de l’application et re-signer l’application et le manifeste de déploiement.

 Les procédures suivantes supposent que votre nom de projet est **ExcelWorkbook** et que vous publiez la solution dans un dossier créé nommé **C: -publier** sur votre ordinateur.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Créer une classe qui définit l'action de post-déploiement

1. Sur la barre de menu, choisissez **File** > **Add** > **New Project**.

2. Dans la boîte de dialogue **Add New Project,** dans la vitre **Des modèles installés,** choisissez le dossier **Windows.**

3. Dans le volet **Templates,** choisissez le modèle **de bibliothèque de classe.**

4. Dans le champ **Nom,** entrez **FileCopyPDA**, puis choisissez le bouton **OK.**

5. Dans **Solution Explorer**, choisissez le projet **FileCopyPDA.**

6. Sur la barre de menu, choisissez **Project** > **Add Reference**.

7. Sur l’onglet **.NET,** ajoutez des références à `Microsoft.VisualStudio.Tools.Applications.Runtime` et `Microsoft.VisualStudio.Tools.Applications.ServerDocument`.

8. Remplacez le nom de la classe par `FileCopyPDA`, puis remplacez le contenu du fichier par le code. Ce code effectue les tâches suivantes :

   - Il copie le document dans le bureau de l'utilisateur.

   - Modifie la _AssemblyLocation propriété d’un chemin relatif à un chemin entièrement qualifié pour le manifeste de déploiement.

   - Il supprime le fichier si l'utilisateur désinstalle la solution.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Générer et publier la solution

1. Dans **Solution Explorer**, ouvrez le menu raccourci pour le projet **FileCopyPDA,** puis choisissez **Build**.

2. Ouvrez le menu raccourci pour le projet **ExcelWorkbook,** puis choisissez **Build**.

3. Ouvrez le menu raccourci pour le projet **ExcelWorkbook,** puis choisissez **Add Reference**.

4. Dans la boîte de dialogue **Add Reference,** choisissez l’onglet **Projets,** choisissez **FileCopyPDA,** puis choisissez le bouton **OK.**

5. Dans **Solution Explorer**, choisissez le projet **ExcelWorkbook.**

6. Sur la barre de menu, choisissez **Project** > **New Folder**.

7. Entrez **les données,** puis choisissez la clé **Enter.**

8. Dans **Solution Explorer**, choisissez le dossier **Data.**

9. Sur la barre de menu, choisissez **Project** > **Ajouter l’article existant**.

10. Dans la boîte de dialogue **Add Existing Item,** naviguez sur l’annuaire de sortie pour le projet **ExcelWorkbook,** choisissez le fichier **ExcelWorkbook.xlsx,** puis choisissez le bouton **Ajouter.**

11. Dans **Solution Explorer,** choisissez le fichier **ExcelWorkbook.xlsx.**

12. Dans la fenêtre **Propriétés,** modifier la propriété **Build Action** en **Contenu** et la propriété Copy to **Output Directory** pour copier si plus **récent**.

     Lorsque vous aurez terminé ces étapes, votre projet ressemblera à l’illustration suivante.

     ![Structure du projet de l'action post-déploiement.](../vsto/media/vsto-postdeployment.png "Structure du projet de l'action post-déploiement.")

13. Publier le projet **ExcelWorkbook.**

### <a name="modify-the-application-manifest"></a>Modifier le manifeste d'application

1. Ouvrez le répertoire de la solution, **c: 'publier**, en utilisant **File Explorer**.

2. Ouvrez le dossier **Fichiers d’application,** puis ouvrez le dossier qui correspond à la version publiée la plus récente de votre solution.

3. Ouvrez le fichier **ExcelWorkbook.dll.manifest** dans un éditeur de texte tel que Notepad.

4. Ajoutez le code suivant après l'élément `</vstav3:update>`. Pour l’attribut `<vstav3:entryPoint>` de classe de l’élément, utilisez la syntaxe suivante: *NamespaceName.ClassName*. Dans l'exemple suivant, les noms de classe et l'espace de noms sont les mêmes, afin que le nom du point d'entrée résultant soit `FileCopyPDA.FileCopyPDA`.

    ```xml
    <vstav3:postActions>
      <vstav3:postAction>
        <vstav3:entryPoint
          class="FileCopyPDA.FileCopyPDA">
          <assemblyIdentity
            name="FileCopyPDA"
            version="1.0.0.0"
            language="neutral"
            processorArchitecture="msil" />
        </vstav3:entryPoint>
        <vstav3:postActionData>
        </vstav3:postActionData>
      </vstav3:postAction>
    </vstav3:postActions>
    ```

### <a name="re-sign-the-application-and-deployment-manifests"></a>Signer à nouveau les manifestes d'application et de déploiement

1. Dans le dossier **de certificat USERPROFILE %-Documents-Visual Studio 2013-Projects-ExcelWorkbook-ExcelWorkbook,** copiez le fichier de certificat **ExcelWorkbook_TemporaryKey.pfx,** puis collez-le dans le dossier *PublishFolder* **'Application Files’ExcelWorkBook**\__MostRecentPublishedVersion._

2. Ouvrez l’invite de commande Visual Studio, puis changez les répertoires pour le dossier **c:'publish’Application Files-ExcelWorkbook**\__MostRecentPublishedVersion_ (par exemple, **c: 'publish’Application Files’ExcelWorkbook_1_0_0_4**).

3. Signez le manifeste d'application modifié en exécutant la commande suivante :

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     Le message « ExcelWorkbook.dll.manifest signé avec succès » s'affiche.

4. Modifier pour le **dossier c : publier,** puis mettre à jour et signer le manifeste de déploiement en exécutant la commande suivante :

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > Dans l’exemple précédent, remplacez MostRecentVersionNumber par le numéro de version de la version la plus récente de votre solution (par exemple, **1 à 00'4**).

     Le message « ExcelWorkbook.vsto signé avec succès » s'affiche.

5. Copiez le fichier *ExcelWorkbook.vsto* à l’annuaire **c:'publish’Application Files’ExcelWorkbook**\__MostRecentVersionNumber._

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a>Mettez le document d’une solution sur un serveur qui exécute SharePoint (personnalisations au niveau des documents seulement)
 Vous pouvez publier votre personnalisation au niveau du document pour les utilisateurs finaux à l'aide de SharePoint. Lorsque les utilisateurs accèdent au site SharePoint et ouvrent le document, le runtime installe automatiquement la solution à partir du dossier réseau partagé sur l'ordinateur local de l'utilisateur. Une fois que la solution est installée localement, la personnalisation fonctionne toujours même si le document est copié ailleurs, sur le bureau par exemple.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Pour placer le document sur un serveur exécutant SharePoint

1. Ajoutez le document de solution à une bibliothèque de documents située sur un site SharePoint.

2. Suivez les étapes de l'une des méthodes suivantes :

    - Utilisez l'outil de configuration d'Office pour ajouter le serveur exécutant SharePoint au Centre de gestion de la confidentialité dans Word ou Excel sur tous les ordinateurs des utilisateurs.

         Voir [les politiques et les paramètres de sécurité dans Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)).

    - Vérifiez que chaque utilisateur effectue les étapes suivantes.

        1. Sur l’ordinateur local, ouvrez Word ou Excel, choisissez **l’onglet Fichier,** puis choisissez le bouton **Options.**

        2. Dans la boîte de dialogue **Trust Center,** choisissez le bouton **Lieux de confiance.**

        3. Sélectionnez les **emplacements fiables Allow sur ma** case à cocher réseau (non recommandée), puis choisissez le nouveau bouton **Ajouter.**

        4. Dans la boîte **De chemin,** entrez l’URL de la bibliothèque de *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*documents SharePoint qui contient le document que vous avez téléchargé (par exemple, ).

             N’ajoutez pas le nom de la page Web par défaut, comme *default.aspx* ou *AllItems.aspx*.

        5. Sélectionnez les **sous-dossiers de cet emplacement sont également cochers de confiance,** puis choisissez le bouton **OK.**

             Lorsque les utilisateurs ouvrent le document du site SharePoint, le document s'ouvre, et la personnalisation est installée. Les utilisateurs peuvent copier le document sur leur bureau. La personnalisation fonctionne toujours car les propriétés du document pointent vers l'emplacement réseau du document.

## <a name="create-a-custom-installer"></a><a name="Custom"></a>Créer un installateur personnalisé
 Vous pouvez créer un installateur personnalisé pour votre solution Office, au lieu d’utiliser le programme de configuration qui vous est créé lorsque vous publiez la solution. Par exemple, vous pouvez utiliser un signe dans le script pour démarrer l’installation, ou vous pouvez utiliser un fichier de lot pour installer la solution sans interaction utilisateur. Ces scénarios conviennent parfaitement si les composants requis sont déjà installés sur les ordinateurs des utilisateurs finaux.

 Dans le cadre de votre processus d’installation personnalisé, appelez l’outil d’installateur pour les solutions Office (*VSTOInstaller.exe*), qui est installé à l’emplacement suivant par défaut :

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Si l’outil n’est pas à cet endroit, vous pouvez utiliser la clé de registre **HKEY_LOCAL_MACHINE-SOFTWARE-MICROSOFT-VSTO Runtime SetupMD v4-InstallerPath** ou **HKEY_LOCAL_MACHINE-SOFTWARE-Wow6432Node-Microsoft-VSTO Runtime SetupMD v4-InstallPath** pour trouver le chemin vers cet outil.

 Vous pouvez utiliser les paramètres suivants avec *VSTOinstaller.exe*.

| Paramètre | Définition |
|------------------| - |
| /Install ou /I | Installe la solution. Vous devez utiliser cette option avec le chemin d'accès d'un manifeste de déploiement. Vous pouvez spécifier un chemin d’accès sur l’ordinateur local, un partage de fichiers UNC (Universal Naming Convention). Vous pouvez spécifier un chemin local (*C: 'FolderName’PublishFolder*), un chemin relatif (*Publier\\*), ou un emplacement entièrement qualifié (*\\'ServerName’FolderName* ou http://<em>ServerName/FolderName</em>). |
| /Uninstall ou /U | Désinstalle la solution. Vous devez utiliser cette option avec le chemin d'accès d'un manifeste de déploiement. Vous pouvez spécifier qu’un chemin d’accès peut se trouver sur l’ordinateur local, un partage de fichiers UNC. Vous pouvez spécifier un chemin local *(c : 'FolderName’PublishFolder*), un chemin relatif (*Publier\\*), ou un emplacement entièrement qualifié (*\\'ServerName’FolderName* ou http://<em>ServerName/FolderName</em>). |
| /Silent ou /S | Installez ou désinstallez sans inviter l'utilisateur à entrer de texte ni afficher de message. Si une invite de fiducie est nécessaire, la personnalisation n’est pas installée ou mise à jour. |
| /Help ou /? | Affiche les informations d'aide. |

 Lorsque vous exécutez *VSTOinstaller.exe*, les codes d’erreur suivants peuvent apparaître.

|Code d'erreur|Définition|
|----------------|----------------|
|0|La solution a été installée ou désinstallée ou l’aide de VSTOInstaller s’est affichée.|
|-100|Une ou plusieurs options de ligne de commande ne sont pas valides ou ont été définies plus d’une fois. Pour plus d’informations, entrez "vstoinstaller /?" ou voir [Créer un installateur personnalisé pour une solution ClickOnce Office](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|
|-101|Une ou plusieurs options de ligne de commande ne sont pas valides. Pour plus d'informations, entrez « vstoinstaller/? ».|
|-200|Le manifeste de déploiement URI n’est pas valide. Pour plus d'informations, entrez « vstoinstaller/? ».|
|-201|La solution n’a pas pu être installée car le manifeste de déploiement n’est pas valide. Voir [les manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|La solution n’a pas pu être installée parce que la section Visual Studio Tools for Office du manifeste de l’application n’est pas valide. Voir [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).|
|-203|La solution n’a pas pu être installée parce qu’une erreur de téléchargement s’est produite. Vérifiez l'URI ou l'emplacement de fichier réseau du manifeste de déploiement et réessayez.|
|-300|La solution n’a pas pu être installée parce qu’une exception de sécurité s’est produite. Voir [les solutions Secure Office](../vsto/securing-office-solutions.md).|
|-400|La solution n’a pas pu être installée.|
|-401|La solution ne pouvait pas être désinstallée.|
|-500|L'opération a été annulée parce que la solution n'a pas pu être installée et désinstallée ou le manifeste de déploiement ne peut pas être téléchargé.|

## <a name="publish-an-update"></a><a name="Update"></a>Publier une mise à jour
 Pour mettre à jour une solution, vous la publiez à nouveau en utilisant le **concepteur de projet** ou **Publiez Wizard,** puis vous copiez la solution mise à jour à l’emplacement de l’installation. Lorsque vous copiez les fichiers dans l'emplacement d'installation, assurez-vous de remplacer les fichiers antérieurs.

 La prochaine fois que la solution vérifie une mise à jour, elle trouvera et chargera automatiquement la nouvelle version.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a>Modifier l’emplacement d’installation d’une solution
 Vous pouvez ajouter ou modifier le chemin d’installation après avoir publié une solution. Vous pourriez vouloir modifier le chemin d’installation pour l’une ou plusieurs des raisons suivantes :

- Le chemin d’installation n’était pas connu lors de la compilation du programme d’installation.

- Les fichiers solution ont été copiés vers un autre emplacement.

- Le serveur qui héberge les fichiers d'installation a un nouveau nom ou emplacement.

  Pour modifier le chemin d'installation d'une solution, vous devez mettre à jour le programme d'installation, puis les utilisateurs doivent l'exécuter. Pour les personnalisations au niveau du document, les utilisateurs doivent également mettre à jour une propriété dans le document pour afficher le nouvel emplacement.

> [!NOTE]
> Si vous ne souhaitez pas demander aux utilisateurs de mettre à jour leurs propriétés de documents, vous pouvez demander aux utilisateurs d’obtenir le document mis à jour à partir du lieu d’installation.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Pour modifier le chemin d’installation dans le programme d’installation

1. Ouvrez une fenêtre **d’invite de commande,** puis changez les répertoires pour le dossier d’installation.

2. Exécutez le programme d'installation et incluez le paramètre `/url`, qui prend le nouveau chemin d'installation comme une chaîne.

    L’exemple suivant indique comment modifier le chemin d’installation dans un emplacement sur le site web Fabrikam, mais vous pouvez remplacer cette URL par le chemin d’accès souhaité :

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Si un message apparaît et indique que la signature du fichier exécutable sera invalidée, le certificat utilisé pour signer la solution n'est plus valide, le serveur de publication est inconnu. Par conséquent, les utilisateurs devront confirmer qu'ils font confiance à la source de la solution avant de pouvoir l'installer.

   > [!NOTE]
   > Pour afficher la valeur actuelle de l'URL, exécutez `setup.exe /url`.

   Pour les personnalisations au niveau des documents, les utilisateurs doivent ouvrir le document, puis mettre à jour sa propriété _AssemblyLocation. Les étapes suivantes décrivent comment les utilisateurs peuvent effectuer cette tâche.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Pour mettre à jour la propriété _AssemblyLocation dans un document

1. Sur l’onglet **Fichier,** choisissez **Info**, ce que l’illustration suivante montre.

     ![Onglet Informations dans Excel](../vsto/media/vsto-infotab.png "Onglet Informations dans Excel")

2. Dans la liste **des propriétés,** choisissez **Advanced Properties**, que l’illustration suivante montre.

     ![Propriétés avancées dans Excel.](../vsto/media/vsto-advanceddocumentproperties.png "Propriétés avancées dans Excel.")

3. Sur l’onglet **Custom** dans la liste **des propriétés,** choisissez _AssemblyLocation, comme le montre l’illustration suivante.

     ![Propriété AssemblyLocation.](../vsto/media/vsto-assemblylocationproperty.png "Propriété AssemblyLocation.")

     La **boîte de valeur** contient l’identifiant manifeste de déploiement.

4. Avant l’identifiant, entrez le chemin entièrement qualifié du document, suivi d’une barre, dans le format *Path*|*Identifier* (par exemple, *File://ServerName/FolderName/FileName|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Pour plus d’informations sur la façon de formater cet identifiant, consultez [l’aperçu des propriétés des documents personnalisés](../vsto/custom-document-properties-overview.md).

5. Choisissez le bouton **OK,** puis enregistrez et fermez le document.

6. Exécutez le programme d'installation sans le paramètre /url pour installer la solution à l'emplacement spécifié.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a>Revenez une solution à une version antérieure
 Lorsque vous restaurez une solution, vous revenez à une version antérieure de cette solution.

#### <a name="to-roll-back-a-solution"></a>Pour restaurer une solution

1. Ouvrez l'emplacement d'installation de la solution.

2. Dans le dossier de publication de haut niveau, supprimez le manifeste de déploiement (le fichier *.vsto).*

3. Recherchez le sous-dossier de la version que vous souhaitez restaurer.

4. Copiez le manifeste de déploiement depuis ce sous-dossier vers le dossier de publication de niveau supérieur.

     Par exemple, pour faire reculer une solution appelée **OutlookAddIn1** de la version 1.0.0.1 à la version 1.0.0.0, copiez le fichier **OutlookAddIn1.vsto** du dossier **OutlookAddIn1_1_0_0_0.** Coller le fichier dans le dossier de publication de haut niveau, en sur-écrivant le manifeste de déploiement spécifique à la version pour **OutlookAddIn1_1_0_0_1** qui était déjà là.

     L’illustration suivante représente la structure des dossiers de publication de cet exemple.

     ![Publier la structure du dossier](../vsto/media/publishfolderstructure.png "Structure du dossier de publication")

     Le changement de manifeste de déploiement sera détecté la prochaine fois qu'un utilisateur ouvre l'application ou le document personnalisé. La version antérieure de la solution Office s'exécute depuis le cache ClickOnce.

> [!NOTE]
> Les données locales ne sont enregistrées que pour la dernière version d'une solution. Si vous annulez deux versions, les données locales ne sont pas conservées. Pour plus d’informations sur les données locales, voir [Accéder aux données locales et à distance dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Voir aussi

- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
- [Publier des solutions Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Comment : Publier une solution Office en utilisant ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Comment : Installer une solution ClickOnce Office](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [Comment : Publier une solution Office au niveau des documents sur un serveur SharePoint en utilisant ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [Créez un installateur personnalisé pour une solution de bureau ClickOnce](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)