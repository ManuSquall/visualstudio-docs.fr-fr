---
title: Déployer une solution Office à l’aide de ClickOnce
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
ms.openlocfilehash: d69e50551f664ab3f3e987f0d113285f50d1315d
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986132"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Déployer une solution Office à l’aide de ClickOnce
  Vous pouvez déployer votre solution Office plus rapidement en utilisant ClickOnce. Si vous publiez des mises à jour, votre solution les détecte et les installe automatiquement. Toutefois, avec ClickOnce, vous devez installer votre solution séparément pour chaque utilisateur d'un ordinateur. Par conséquent, vous devez envisager d’utiliser Windows Installer ( *. msi*) si plusieurs utilisateurs exécutent votre solution sur le même ordinateur.

## <a name="in-this-topic"></a>Dans cette rubrique

- [Publier la solution](#Publish)

- [Décider de la façon dont vous souhaitez accorder la confiance à la solution](#Trust)

- [Aider les utilisateurs à installer la solution](#Helping)

- [Placer le document d’une solution sur l’ordinateur de l’utilisateur final (personnalisations au niveau du document uniquement)](#Put)

- [Placer le document d’une solution sur un serveur qui exécute SharePoint (personnalisations au niveau du document uniquement)](#SharePoint)

- [Créer un programme d’installation personnalisé](#Custom)

- [Publier une mise à jour](#Update)

- [Modifier l’emplacement d’installation d’une solution](#Location)

- [Restaurer une version antérieure d’une solution](#Roll)

  Pour plus d’informations sur le déploiement d’une solution Office en créant un fichier Windows Installer, consultez [déployer une solution Office à l’aide d’Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="Publish"></a>Publier la solution
 Vous pouvez publier votre solution à l’aide de l' **Assistant Publication** ou du **Concepteur de projet**. Dans cette procédure, vous allez utiliser le **Concepteur de projets** , car il fournit l’ensemble complet des options de publication. Consultez [Assistant &#40;publication dans le développement Office dans&#41;Visual Studio](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Pour publier la solution

1. Dans **Explorateur de solutions**, choisissez le nœud nommé pour votre projet.

2. Dans la barre de menus, choisissez **projet**, **Propriétés** *ProjectName* .

3. Dans le **Concepteur de projet**, choisissez l’onglet **publier** , comme le montre l’illustration suivante.

    ![Onglet publier du concepteur de projets](../vsto/media/vsto-publishtab.png "Onglet Publier du Concepteur de projets")

4. Dans la zone **emplacement du dossier de publication (serveur FTP ou chemin d’accès du fichier)** , entrez le chemin d’accès du dossier dans lequel vous souhaitez que le **Concepteur de projets** copie les fichiers solution.

    Vous pouvez entrer n'importe lequel des types de chemins d'accès suivants.

   - Un chemin d’accès local (par exemple, *c:\NomDossier\NomDossier*).

   - Un chemin d’accès UNC (Uniform Naming Convention) à un dossier sur votre réseau (par exemple, *\\\ServerName\FolderName*).

   - Un chemin d’accès relatif (par exemple, *dossierpublication\\* , qui est le dossier dans lequel le projet est publié par défaut).

5. Dans la zone **URL du dossier d’installation** , entrez le chemin d’accès complet de l’emplacement où l’utilisateur final trouvera votre solution.

    Si vous ne connaissez pas encore l’emplacement, n’entrez rien dans ce champ. Par défaut, ClickOnce recherche des mises à jour dans le dossier à partir duquel les utilisateurs installent la solution.

6. Choisissez le bouton **Composants requis** .

7. Dans la boîte de dialogue composants **requis** , assurez-vous que la case à cocher **créer un programme d’installation des composants requis** est activée.

8. Dans la liste **choisir les composants requis à installer** , activez les cases à cocher pour **Windows Installer 4,5** et le package de .NET Framework approprié.

    Par exemple, si votre solution cible le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], activez les cases à cocher **Windows Installer 4,5** et **Microsoft .NET Framework 4,5 complet**.

9. Si votre solution cible le .NET Framework 4,5, activez également la case à cocher **Visual Studio 2010 Tools pour Office Runtime** .

    > [!NOTE]
    > Par défaut, cette case à cocher ne s’affiche pas. Pour afficher cette case à cocher, vous devez créer un package de programme d'amorçage. Consultez [créer un package de programme d’amorçage pour un complément VSTO Office 2013 avec Visual Studio 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md).

10. Sous **Spécifiez l’emplacement d’installation des composants requis**, choisissez l’une des options qui s’affiche, puis choisissez le bouton **OK** .

     Le tableau suivant décrit chaque option.

    |Option|Description|
    |------------|-----------------|
    |**Télécharger les composants requis à partir du site web du fournisseur de composants**|L'utilisateur est invité à télécharger et à installer les composants requis du fournisseur.|
    |**Télécharger les composants requis à partir de l’emplacement de mon application**|Les logiciels requis sont installés avec la solution. Si vous choisissez cette option, Visual Studio copie tous les packages de composants requis dans l'emplacement de publication à votre place. Pour que cette option fonctionne, les packages de composants requis doivent être sur l'ordinateur de développement.|
    |**Télécharger les composants requis depuis l’emplacement suivant**|Visual Studio copie tous les packages de composants requis dans l'emplacement que vous spécifiez et les installe avec la solution.|

     Consultez [la boîte de dialogue composants requis](../ide/reference/prerequisites-dialog-box.md).

11. Cliquez sur le bouton **mises à jour** , spécifiez la fréquence à laquelle vous souhaitez que le complément ou la personnalisation VSTO de chaque utilisateur final vérifie les mises à jour, puis choisissez le bouton **OK** .

    > [!NOTE]
    > Si vous effectuez le déploiement à l’aide d’un CD ou d’un lecteur amovible, choisissez la case **d’option ne jamais Rechercher les mises à jour** .

     Pour plus d’informations sur la publication d’une mise à jour, consultez [publier une mise à jour](#Update).

12. Choisissez le bouton **options** , passez en revue les options de la boîte de dialogue **options** , puis choisissez le bouton **OK** .

13. Choisissez le bouton **publier maintenant** .

     Visual Studio ajoute les dossiers et les fichiers suivants au dossier de publication que vous avez spécifié précédemment dans cette procédure.

    - Dossier des **fichiers d’application** .

    - Le programme d'installation.

    - Un manifeste de déploiement qui pointe vers le manifeste de déploiement de la version la plus récente.

      Le dossier **fichiers d’application** contient un sous-dossier pour chaque version que vous publiez. Chaque sous-dossier spécifique à la version contient les fichiers suivants.

    - Un manifeste d’application.

    - Un manifeste de déploiement.

    - Des assemblys de personnalisation.

      L'illustration suivante représente la structure du dossier de publication pour un complément VSTO Outlook.

      ![Structure du dossier de publication](../vsto/media/publishfolderstructure.png "Structure du dossier de publication")

    > [!NOTE]
    > ClickOnce ajoute l’extension *. deploy* aux assemblys afin qu’une installation sécurisée de Internet Information Services (IIS) ne bloque pas les fichiers en raison d’une extension non sécurisée. Lorsque l’utilisateur installe la solution, ClickOnce supprime l’extension *. deploy* .

14. Copiez les fichiers solution dans l'emplacement d'installation que vous avez spécifié précédemment dans cette procédure.

## <a name="Trust"></a>Décider de la façon dont vous souhaitez accorder la confiance à la solution
 Avant qu'une solution puisse s'exécuter sur les ordinateurs des utilisateurs, vous devez soit accorder votre confiance soit les utilisateurs doivent répondre à une invite d'approbation lorsqu'ils installent la solution. Pour accorder un niveau de confiance à la solution, signez les manifestes à l'aide d'un certificat qui identifie un éditeur connu et approuvé. Consultez [approuver la solution en signant les manifestes d’application et de déploiement](../vsto/granting-trust-to-office-solutions.md#Signing).

 Si vous déployez une personnalisation au niveau du document et que vous souhaitez placer le document dans un dossier sur l’ordinateur de l’utilisateur ou rendre le document disponible sur un site SharePoint, assurez-vous qu’Office approuve l’emplacement du document. Consultez [accorder un niveau de confiance à des documents](../vsto/granting-trust-to-documents.md).

## <a name="Helping"></a>Aider les utilisateurs à installer la solution
 Les utilisateurs peuvent installer la solution en exécutant le programme d’installation, en ouvrant le manifeste de déploiement, ou pendant la personnalisation au niveau du document, en ouvrant le document directement. Il est recommandé que les utilisateurs installent votre solution à l'aide du programme d'installation. Les deux autres approches ne garantissent pas que les logiciels requis sont installés. Si les utilisateurs souhaitent ouvrir le document à partir de l'emplacement d'installation, ils doivent l'ajouter à la liste des emplacements approuvés dans le Centre de gestion de la confidentialité des applications Office.

### <a name="opening-the-document-of-a-document-level-customization"></a>Ouverture du document d'une personnalisation au niveau du document
 Les utilisateurs peuvent ouvrir le document d'une personnalisation au niveau du document à partir de l'emplacement d'installation ou en copiant le document sur leur ordinateur local, puis en ouvrant la copie.

 Il est recommandé que les utilisateurs ouvrent une copie du document sur leurs ordinateurs afin que plusieurs utilisateurs n'essayent pas d'ouvrir la même copie simultanément. Pour mettre en œuvre ce principe, vous pouvez configurer votre programme d'installation pour copier le document sur les ordinateurs d'utilisateur. Consultez [Placer le document d’une solution sur l’ordinateur de l’utilisateur final (personnalisations au niveau du document uniquement)](#Put).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Installer la solution en ouvrant le manifeste de déploiement à partir d’un site Web IIS
 Les utilisateurs peuvent installer une solution Office en ouvrant le manifeste de déploiement à partir du Web. Toutefois, une installation sécurisée de Internet Information Services (IIS) bloquera les fichiers portant l’extension *. vsto* . Le type MIME doit être défini dans IIS avant de pouvoir déployer une solution Office à l'aide d'IIS.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Pour ajouter le type MIME .vsto à IIS 6.0

1. Sur le serveur qui exécute IIS 6,0, choisissez **démarrer** > **tous les programmes** > **Outils d’administration** >  **Gestionnaire de Internet Information Services (IIS)** .

2. Choisissez le nom de l’ordinateur, le dossier **sites Web** ou le site Web que vous configurez.

3. Dans la barre de menus, choisissez **Action** > **Propriétés**.

4. Dans l’onglet **en-têtes http** , choisissez le bouton **types MIME** .

5. Dans la fenêtre **types MIME** , choisissez le bouton **nouveau** .

6. Dans la fenêtre **type MIME** , entrez **. vsto** comme extension, entrez **application/x-ms-vsto** comme type MIME, puis appliquez les nouveaux paramètres.

    > [!NOTE]
    > Pour que les modifications soient prises en compte, vous devez redémarrer le service de publication World Wide Web ou attendre le recyclage du processus de travail. Vous devez ensuite vider le cache disque du navigateur, puis essayer à nouveau d’ouvrir le fichier *. vsto* .

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Pour ajouter le type MIME .vsto à IIS 7,0

1. Sur le serveur qui exécute IIS 7,0, choisissez **démarrer** > **tous les programmes** > **accessoires**.

2. Ouvrez le menu contextuel de l' **invite de commandes**, puis choisissez **exécuter en tant qu’administrateur.**

3. Dans la zone **ouvrir** , entrez le chemin d’accès suivant, puis choisissez le bouton **OK** .

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Entrez la commande suivante, puis appliquez les nouveaux paramètres.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Pour que les modifications soient prises en compte, vous devez redémarrer le service de publication World Wide Web ou attendre le recyclage du processus de travail. Vous devez ensuite vider le cache disque du navigateur, puis essayer à nouveau d’ouvrir le fichier *. vsto* .

## <a name="Put"></a>Placer le document d’une solution sur l’ordinateur de l’utilisateur final (personnalisations au niveau du document uniquement)
 Vous pouvez copier le document de votre solution sur l’ordinateur de l’utilisateur final en créant une action de postconnexion. De cette façon, l’utilisateur n’a pas besoin de copier manuellement le document à partir de l’emplacement d’installation sur son ordinateur après l’installation de votre solution. Vous devrez créer une classe qui définit l’action de postconnexion, générer et publier la solution, modifier le manifeste d’application et signer à nouveau le manifeste d’application et de déploiement.

 Les procédures suivantes supposent que le nom de votre projet est **ExcelWorkbook** et que vous publiez la solution dans un dossier créé nommé **C:\publish** sur votre ordinateur.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Créer une classe qui définit l'action de post-déploiement

1. Dans la barre de menus, choisissez **fichier**  > **Ajouter**  > **nouveau projet**.

2. Dans la boîte de dialogue **Ajouter un nouveau projet** , dans le volet **modèles installés** , choisissez le dossier **Windows** .

3. Dans le volet **modèles** , choisissez le modèle **bibliothèque de classes** .

4. Dans le champ **nom** , entrez **FileCopyPDA**, puis choisissez le bouton **OK** .

5. Dans **Explorateur de solutions**, choisissez le projet **FileCopyPDA** .

6. Dans la barre de menus, choisissez **Projet** > **Ajouter une référence**.

7. Sous l’onglet **.net** , ajoutez des références à `Microsoft.VisualStudio.Tools.Applications.Runtime` et `Microsoft.VisualStudio.Tools.Applications.ServerDocument`.

8. Remplacez le nom de la classe par `FileCopyPDA`, puis remplacez le contenu du fichier par le code. Ce code exécute les tâches suivantes :

   - Il copie le document dans le bureau de l'utilisateur.

   - Remplace la propriété _ AssemblyLocation d’un chemin d’accès relatif par un chemin d’accès qualifié complet pour le manifeste de déploiement.

   - Il supprime le fichier si l'utilisateur désinstalle la solution.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Générer et publier la solution

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **FileCopyPDA** , puis choisissez **générer**.

2. Ouvrez le menu contextuel du projet **ExcelWorkbook** , puis choisissez **générer**.

3. Ouvrez le menu contextuel du projet **ExcelWorkbook** , puis choisissez **Ajouter une référence**.

4. Dans la boîte de dialogue **Ajouter une référence** , choisissez l’onglet **projets** , puis sélectionnez **FileCopyPDA**et le bouton **OK** .

5. Dans **Explorateur de solutions**, choisissez le projet **ExcelWorkbook** .

6. Dans la barre de menus, choisissez **projet** > **nouveau dossier**.

7. Entrez des **données**, puis appuyez sur la touche **entrée** .

8. Dans **Explorateur de solutions**, choisissez le dossier **données** .

9. Dans la barre de menus, choisissez **projet** > **Ajouter un élément existant**.

10. Dans la boîte de dialogue **Ajouter un élément existant** , accédez au répertoire de sortie du projet **ExcelWorkbook** , choisissez le fichier **ExcelWorkbook. xlsx** , puis cliquez sur le bouton **Ajouter** .

11. Dans **Explorateur de solutions** choisissez le fichier **ExcelWorkbook. xlsx** .

12. Dans la fenêtre **Propriétés** , affectez à la propriété **action de génération** la valeur **contenu** et à la propriété **copier dans le répertoire de sortie** la valeur **copier si plus récent**.

     Une fois ces étapes effectuées, votre projet ressemble à l’illustration suivante.

     ![Structure de projet de l’action de publication du déploiement.](../vsto/media/vsto-postdeployment.png "Structure du projet de l'action post-déploiement.")

13. Publiez le projet **ExcelWorkbook** .

### <a name="modify-the-application-manifest"></a>Modifier le manifeste d'application

1. Ouvrez le répertoire de la solution, **c:\publish**, à l’aide de l' **Explorateur de fichiers**.

2. Ouvrez le dossier **fichiers d’application** , puis ouvrez le dossier qui correspond à la version publiée la plus récente de votre solution.

3. Ouvrez le fichier **ExcelWorkbook. dll. manifest** dans un éditeur de texte tel que le bloc-notes.

4. Ajoutez le code suivant après l'élément `</vstav3:update>`. Pour l’attribut Class de l’élément `<vstav3:entryPoint>`, utilisez la syntaxe suivante : *NomEspaceNoms. ClassName*. Dans l'exemple suivant, les noms de classe et l'espace de noms sont les mêmes, afin que le nom du point d'entrée résultant soit `FileCopyPDA.FileCopyPDA`.

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

1. Dans le dossier **%USERPROFILE%\Documents\Visual Studio 2013 \ Projects\ExcelWorkbook\ExcelWorkbook** , copiez le fichier de certificat **ExcelWorkbook_TemporaryKey. pfx** , puis collez-le dans le *DossierPublication* **\Application Files \ Dossier ExcelWorkbook**\__dernièreversionpubliée_ .

2. Ouvrez l’invite de commandes de Visual Studio, puis accédez au dossier **C:\publish\Application Files\ExcelWorkbook**\__dernièreversionpubliée_ (par exemple, **c:\publish\Application Files\ExcelWorkbook_1_0_0 _4**).

3. Signez le manifeste d'application modifié en exécutant la commande suivante :

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     Le message « ExcelWorkbook.dll.manifest signé avec succès » s'affiche.

4. Accédez au dossier **c:\publish** , puis mettez à jour et signez le manifeste de déploiement en exécutant la commande suivante :

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > Dans l’exemple précédent, remplacez MostRecentVersionNumber par le numéro de version de la dernière version publiée de votre solution (par exemple, **1_0_0_4**).

     Le message « ExcelWorkbook.vsto signé avec succès » s'affiche.

5. Copiez le fichier *ExcelWorkbook. vsto* dans le répertoire **C:\publish\Application Files\ExcelWorkbook**\__MostRecentVersionNumber_ .

## <a name="SharePoint"></a>Placer le document d’une solution sur un serveur qui exécute SharePoint (personnalisations au niveau du document uniquement)
 Vous pouvez publier votre personnalisation au niveau du document pour les utilisateurs finaux à l'aide de SharePoint. Lorsque les utilisateurs accèdent au site SharePoint et ouvrent le document, le runtime installe automatiquement la solution à partir du dossier réseau partagé sur l'ordinateur local de l'utilisateur. Une fois que la solution est installée localement, la personnalisation fonctionne toujours même si le document est copié ailleurs, sur le bureau par exemple.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Pour placer le document sur un serveur exécutant SharePoint

1. Ajoutez le document de solution à une bibliothèque de documents située sur un site SharePoint.

2. Suivez les étapes de l'une des méthodes suivantes :

    - Utilisez l'outil de configuration d'Office pour ajouter le serveur exécutant SharePoint au Centre de gestion de la confidentialité dans Word ou Excel sur tous les ordinateurs des utilisateurs.

         Consultez [stratégies et paramètres de sécurité dans Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)).

    - Vérifiez que chaque utilisateur effectue les étapes suivantes.

        1. Sur l’ordinateur local, ouvrez Word ou Excel, choisissez l’onglet **fichier** , puis cliquez sur le bouton **options** .

        2. Dans la boîte de dialogue Centre de gestion de la **confidentialité** , choisissez le bouton **emplacements approuvés** .

        3. Activez la case à cocher **autoriser les emplacements approuvés sur mon réseau (non recommandé)** , puis cliquez sur le bouton **Ajouter un nouvel emplacement** .

        4. Dans la zone **chemin d’accès** , entrez l’URL de la bibliothèque de documents SharePoint qui contient le document que vous avez téléchargé (par exemple, *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName* ).

             N’ajoutez pas le nom de la page Web par défaut, par exemple *default. aspx* ou *AllItems. aspx*.

        5. Activez la case à cocher les **sous-dossiers de cet emplacement sont également approuvés** , puis choisissez le bouton **OK** .

             Lorsque les utilisateurs ouvrent le document du site SharePoint, le document s'ouvre, et la personnalisation est installée. Les utilisateurs peuvent copier le document sur leur bureau. La personnalisation fonctionne toujours car les propriétés du document pointent vers l'emplacement réseau du document.

## <a name="Custom"></a>Créer un programme d’installation personnalisé
 Vous pouvez créer un programme d’installation personnalisé pour votre solution Office, au lieu d’utiliser le programme d’installation créé pour vous lorsque vous publiez la solution. Par exemple, vous pouvez utiliser un script de connexion pour démarrer l’installation, ou vous pouvez utiliser un fichier de commandes pour installer la solution sans intervention de l’utilisateur. Ces scénarios conviennent parfaitement si les composants requis sont déjà installés sur les ordinateurs des utilisateurs finaux.

 Dans le cadre de votre processus d’installation personnalisée, appelez l’outil installer pour les solutions Office (*VSTOInstaller. exe*), qui est installé à l’emplacement suivant par défaut :

 *%COMMONPROGRAMFILES%\Microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Si l’outil ne se trouve pas dans cet emplacement, vous pouvez utiliser le Registre **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath** ou **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath** clé pour rechercher le chemin d’accès à cet outil.

 Vous pouvez utiliser les paramètres suivants avec *VSTOInstaller. exe*.

| Paramètre | Définition |
|------------------| - |
| /Install ou /I | Installe la solution. Vous devez utiliser cette option avec le chemin d'accès d'un manifeste de déploiement. Vous pouvez spécifier un chemin d’accès sur l’ordinateur local, un partage de fichiers UNC (Universal Naming Convention). Vous pouvez spécifier un chemin d’accès local (*c:\nomdossier\dossierpublication*), un chemin d’accès relatif (*publication\\* ) ou un emplacement complet ( *\\\ServerName\FolderName* ou http://<em>nomserveur/nomdossier</em>). |
| /Uninstall ou /U | Désinstalle la solution. Vous devez utiliser cette option avec le chemin d'accès d'un manifeste de déploiement. Vous pouvez spécifier qu’un chemin d’accès peut se trouver sur l’ordinateur local, un partage de fichiers UNC. Vous pouvez spécifier un chemin d’accès local (*c:\nomdossier\dossierpublication*), un chemin d’accès relatif (*publication\\* ) ou un emplacement complet ( *\\\ServerName\FolderName* ou http://<em>nomserveur/nomdossier</em>). |
| /Silent ou /S | Installez ou désinstallez sans inviter l'utilisateur à entrer de texte ni afficher de message. Si une invite d’approbation est requise, la personnalisation n’est pas installée ou mise à jour. |
| /Help ou /? | Affiche les informations d'aide. |

 Quand vous exécutez *VSTOInstaller. exe*, les codes d’erreur suivants peuvent s’afficher.

|Code d'erreur|Définition|
|----------------|----------------|
|0|La solution a été installée ou désinstallée ou l’aide de VSTOInstaller s’est affichée.|
|-100|Une ou plusieurs options de ligne de commande ne sont pas valides ou ont été définies plusieurs fois. Pour plus d’informations, entrez « VSTOInstaller/ ? » ou consultez [créer un programme d’installation personnalisé pour une solution Office ClickOnce](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|
|-101|Une ou plusieurs options de ligne de commande ne sont pas valides. Pour plus d'informations, entrez « vstoinstaller/? ».|
|-200|L’URI du manifeste de déploiement n’est pas valide. Pour plus d'informations, entrez « vstoinstaller/? ».|
|-201|Impossible d’installer la solution, car le manifeste de déploiement n’est pas valide. Consultez [manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|La solution n’a pas pu être installée, car la section Visual Studio Tools pour Office du manifeste de l’application n’est pas valide. Consultez [manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).|
|-203|La solution n’a pas pu être installée car une erreur de téléchargement s’est produite. Vérifiez l'URI ou l'emplacement de fichier réseau du manifeste de déploiement et réessayez.|
|-300|La solution n’a pas pu être installée car une exception de sécurité s’est produite. Consultez [sécuriser des solutions Office](../vsto/securing-office-solutions.md).|
|-400|La solution n’a pas pu être installée.|
|-401|La solution n’a pas pu être désinstallée.|
|-500|L'opération a été annulée parce que la solution n'a pas pu être installée et désinstallée ou le manifeste de déploiement ne peut pas être téléchargé.|

## <a name="Update"></a>Publier une mise à jour
 Pour mettre à jour une solution, vous devez la publier à nouveau à l’aide du **Concepteur de projets** ou de l' **Assistant Publication**, puis copier la solution mise à jour à l’emplacement d’installation. Lorsque vous copiez les fichiers dans l'emplacement d'installation, assurez-vous de remplacer les fichiers antérieurs.

 La prochaine fois que la solution recherchera une mise à jour, elle trouvera et chargera automatiquement la nouvelle version.

## <a name="Location"></a>Modifier l’emplacement d’installation d’une solution
 Vous pouvez ajouter ou modifier le chemin d’installation après avoir publié une solution. Vous pourriez vouloir modifier le chemin d’installation pour l’une ou plusieurs des raisons suivantes :

- Le chemin d’installation n’était pas connu lors de la compilation du programme d’installation.

- Les fichiers solution ont été copiés vers un autre emplacement.

- Le serveur qui héberge les fichiers d'installation a un nouveau nom ou emplacement.

  Pour modifier le chemin d'installation d'une solution, vous devez mettre à jour le programme d'installation, puis les utilisateurs doivent l'exécuter. Pour les personnalisations au niveau du document, les utilisateurs doivent également mettre à jour une propriété dans le document pour afficher le nouvel emplacement.

> [!NOTE]
> Si vous ne souhaitez pas demander aux utilisateurs de mettre à jour leurs propriétés de document, vous pouvez demander aux utilisateurs d’obtenir le document mis à jour à partir de l’emplacement d’installation.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Pour modifier le chemin d’installation dans le programme d’installation

1. Ouvrez une fenêtre d' **invite de commandes** , puis accédez au dossier d’installation.

2. Exécutez le programme d'installation et incluez le paramètre `/url`, qui prend le nouveau chemin d'installation comme une chaîne.

    L’exemple suivant indique comment modifier le chemin d’installation dans un emplacement sur le site web Fabrikam, mais vous pouvez remplacer cette URL par le chemin d’accès souhaité :

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Si un message apparaît et indique que la signature du fichier exécutable sera invalidée, le certificat utilisé pour signer la solution n'est plus valide, le serveur de publication est inconnu. Par conséquent, les utilisateurs devront confirmer qu'ils font confiance à la source de la solution avant de pouvoir l'installer.

   > [!NOTE]
   > Pour afficher la valeur actuelle de l'URL, exécutez `setup.exe /url`.

   Pour les personnalisations au niveau du document, les utilisateurs doivent ouvrir le document, puis mettre à jour sa propriété _ AssemblyLocation. Les étapes suivantes décrivent comment les utilisateurs peuvent effectuer cette tâche.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Pour mettre à jour la propriété _AssemblyLocation dans un document

1. Dans l’onglet **fichier** , choisissez **info**, comme le montre l’illustration suivante.

     ![Onglet info dans Excel](../vsto/media/vsto-infotab.png "Onglet Informations dans Excel")

2. Dans la liste **Propriétés** , choisissez **Propriétés avancées**, comme le montre l’illustration suivante.

     ![Propriétés avancées dans Excel.](../vsto/media/vsto-advanceddocumentproperties.png "Propriétés avancées dans Excel.")

3. Dans l’onglet **personnalisé** de la liste **Propriétés** , choisissez _ AssemblyLocation, comme le montre l’illustration suivante.

     ![Propriété AssemblyLocation.](../vsto/media/vsto-assemblylocationproperty.png "Propriété AssemblyLocation.")

     La zone **valeur** contient l’identificateur du manifeste de déploiement.

4. Avant l’identificateur, entrez le chemin d’accès complet du document, suivi d’une barre, dans le *chemin* de format|*identificateur* (par exemple, *file://servername/FolderName/filename|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Pour plus d’informations sur la façon de mettre en forme cet identificateur, consultez [vue d’ensemble des propriétés de document personnalisé](../vsto/custom-document-properties-overview.md).

5. Choisissez le bouton **OK** , puis enregistrez et fermez le document.

6. Exécutez le programme d'installation sans le paramètre /url pour installer la solution à l'emplacement spécifié.

## <a name="Roll"></a>Restaurer une version antérieure d’une solution
 Lorsque vous restaurez une solution, vous revenez à une version antérieure de cette solution.

#### <a name="to-roll-back-a-solution"></a>Pour restaurer une solution

1. Ouvrez l'emplacement d'installation de la solution.

2. Dans le dossier de publication de niveau supérieur, supprimez le manifeste de déploiement (fichier *. vsto* ).

3. Recherchez le sous-dossier de la version que vous souhaitez restaurer.

4. Copiez le manifeste de déploiement depuis ce sous-dossier vers le dossier de publication de niveau supérieur.

     Par exemple, pour restaurer une solution appelée **OutlookAddIn1** , de la version 1.0.0.1 à la version 1.0.0.0, copiez le fichier **OutlookAddIn1. vsto** à partir du dossier **OutlookAddIn1_1_0_0_0** Collez le fichier dans le dossier de publication de niveau supérieur, en remplaçant le manifeste de déploiement spécifique à la version pour **OutlookAddIn1_1_0_0_1** déjà présent.

     L’illustration suivante représente la structure des dossiers de publication de cet exemple.

     ![Structure du dossier de publication](../vsto/media/publishfolderstructure.png "Structure du dossier de publication")

     Le changement de manifeste de déploiement sera détecté la prochaine fois qu'un utilisateur ouvre l'application ou le document personnalisé. La version antérieure de la solution Office s'exécute depuis le cache ClickOnce.

> [!NOTE]
> Les données locales ne sont enregistrées que pour la dernière version d'une solution. Si vous restaurez deux versions, les données locales ne sont pas conservées. Pour plus d’informations sur les données locales, consultez [accéder aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Voir aussi

- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
- [Publier des solutions Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Comment : publier une solution Office à l’aide de ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Comment : installer une solution Office ClickOnce](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [Comment : publier une solution Office au niveau du document sur un serveur SharePoint à l’aide de ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [Créer un programme d’installation personnalisé pour une solution Office ClickOnce](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)