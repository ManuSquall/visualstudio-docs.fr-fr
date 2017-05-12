---
title: "D&#233;ploiement d&#39;une solution Office &#224; l&#39;aide de ClickOnce"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "déploiement ClickOnce (développement Office dans Visual Studio), déployer des solutions"
  - "développement Office dans Visual Studio, déployer des solutions"
ms.assetid: feb516b3-5e4d-449a-9fd2-347d08d90252
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 58
---
# D&#233;ploiement d&#39;une solution Office &#224; l&#39;aide de ClickOnce
  Vous pouvez déployer votre solution Office plus rapidement en utilisant ClickOnce.  Si vous publiez des mises à jour, votre solution les détecte et les installe automatiquement.  Toutefois, avec ClickOnce, vous devez installer votre solution séparément pour chaque utilisateur d'un ordinateur.  Vous devez donc plutôt utiliser Windows Installer \(.msi\) si plusieurs utilisateurs exécutent votre solution sur le même ordinateur.  
  
## Dans cette rubrique  
  
-   [Publier la solution](#Publish)  
  
-   [Déterminer comment accorder un niveau de confiance à la solution](#Trust)  
  
-   [Aider les utilisateurs à installer la solution](#Helping)  
  
-   [Placer le document d'une solution sur l'ordinateur de l'utilisateur final (personnalisations au niveau du document uniquement)](#Put)  
  
-   [Placer le document d'une solution sur un serveur exécutant SharePoint (personnalisations au niveau du document uniquement)](#SharePoint)  
  
-   [Créer un programme d'installation personnalisé](#Custom)  
  
-   [Publier une mise à jour](#Update)  
  
-   [Modifier l'emplacement d'installation d'une solution](#Location)  
  
-   [Restaurer la version antérieure d'une solution](#Roll)  
  
 Pour plus d'informations sur la manière de déployer une solution Office en créant un fichier Windows Installer, consultez [Déploiement d'une solution Office à l'aide de Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Publish"></a> Publier la solution  
 Vous pouvez publier votre solution à l'aide de l'**Assistant Publication** ou du **Concepteur de projets**.  Dans cette procédure, vous utiliserez le **Concepteur de projets** car il fournit l'ensemble complet des options de publication.  Consultez [Assistant Publication &#40;Développement Office dans Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).  
  
#### Pour publier la solution  
  
1.  Dans l'**Explorateur de solutions**, choisissez le nœud correspondant au nom de votre projet.  
  
2.  Dans la barre de menus, choisissez **Projet**, *Propriétés* **NomProjet**.  
  
3.  Dans **Concepteur de projets**, choisissez l'onglet **Publier** figurant dans l'illustration suivante.  
  
     ![Onglet Publier du Concepteur de projets](../vsto/media/vsto-publishtab.png "Onglet Publier du Concepteur de projets")  
  
4.  Dans la zone **Emplacement du dossier de publication \(serveur FTP ou chemin d'accès du fichier\)**, entrez le chemin d'accès au dossier dans lequel vous souhaitez que le **Concepteur de projets** copie les fichiers solution.  
  
     Vous pouvez entrer n'importe lequel des types de chemins d'accès suivants.  
  
    -   Un chemin d'accès local \(par exemple, *C:\\NomDossier\\NomDossier*\).  
  
    -   Un chemin d'accès au format UNC \(Uniform Naming Convention\) sur un dossier de votre réseau \(par exemple, *\\\\NomServeur\\NomDossier*\).  
  
    -   Un chemin d'accès relatif \(par exemple, *DossierPublication\\*, qui est le dossier dans lequel le projet est publié par défaut\).  
  
5.  Dans la zone **URL du dossier d'installation**, entrez le chemin d'accès complet de l'emplacement où l'utilisateur final pourra trouver votre solution.  
  
     Si vous ne connaissez pas encore l'emplacement, n'entrez rien dans ce champ.  Par défaut, ClickOnce recherche des mises à jour dans le dossier à partir duquel les utilisateurs installent la solution.  
  
6.  Choisissez le bouton **Composants requis**.  
  
7.  Dans la boîte de dialogue **Composants requis**, vérifiez que la case à cocher **Créer un programme d'installation des composants requis** est activée.  
  
8.  Dans la liste **Choisir les composants requis à installer**, activez les cases à cocher en regard de **Windows Installer 4.5** et le package .NET Framework approprié.  
  
     Par exemple, si votre solution cible [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], activez la case à cocher en regard de **Windows Installer 4.5** et **Microsoft .NET Framework 4.5 Full**.  
  
9. Si votre solution cible .NET Framework 4.5, activez également la case à cocher en regard de **Visual Studio 2010 Tools for Office Runtime**.  
  
    > [!NOTE]  
    >  Par défaut, cette case à cocher n'apparaît pas.  Pour afficher cette case à cocher, vous devez créer un package de programme d'amorçage.  Consultez [Création d'un package de programme d'amorçage pour un complément VSTO Office 2013 avec Visual Studio 2012](http://blogs.msdn.com/b/vsto/archive/2012/12/21/creating-a-bootstrapper-package-for-an-office-2013-vsto-add-in-with-visual-studio-2012.aspx).  
  
10. Sous **Spécifier l'emplacement d'installation des composants requis**, choisissez l'une des options affichées, puis choisissez le bouton **OK**.  
  
     Le tableau suivant décrit chaque option.  
  
    |Option|Description|  
    |------------|-----------------|  
    |**Télécharger les composants requis à partir du site Web du fournisseur de composants**|L'utilisateur est invité à télécharger et à installer les composants requis du fournisseur.|  
    |**Télécharger les composants requis à partir de l'emplacement de mon application**|Les logiciels requis sont installés avec la solution.  Si vous choisissez cette option, Visual Studio copie tous les packages de composants requis dans l'emplacement de publication à votre place.  Pour que cette option fonctionne, les packages de composants requis doivent être sur l'ordinateur de développement.|  
    |**Télécharger les composants requis depuis l'emplacement suivant**|Visual Studio copie tous les packages de composants requis dans l'emplacement que vous spécifiez et les installe avec la solution.|  
  
     Consultez [Composants requis, boîte de dialogue](../ide/reference/prerequisites-dialog-box.md).  
  
11. Cliquez sur le bouton **Mises à jour**, spécifiez la fréquence à laquelle vous souhaitez que le complément VSTO ou la personnalisation de chaque utilisateur final vérifie la présence de mises à jour, puis choisissez le bouton **OK**.  
  
    > [!NOTE]  
    >  Si vous effectuez un déploiement à l'aide d'un CD ou d'un lecteur amovible, choisissez la case d'option **Ne jamais vérifier**.  
  
     Pour savoir comment publier une mise à jour, consultez [Publier une mise à jour](#Update).  
  
12. Choisissez le bouton **Options**, passez en revue les options de la boîte de dialogue **Options**, puis choisissez le bouton **OK**.  
  
13. Choisissez le bouton **Publier maintenant**.  
  
     Visual Studio ajoute les dossiers et les fichiers suivants au dossier de publication que vous avez spécifié précédemment dans cette procédure.  
  
    -   Le dossier**Fichiers d'application**.  
  
    -   Le programme d'installation.  
  
    -   Un manifeste de déploiement qui pointe vers le manifeste de déploiement de la version la plus récente.  
  
     Le dossier **Fichiers d'application** contient un sous\-dossier pour chaque version que vous publiez.  Chaque sous\-dossier spécifique à la version contient les fichiers suivants.  
  
    -   Un manifeste d'application.  
  
    -   Un manifeste de déploiement.  
  
    -   Des assemblys de personnalisation.  
  
     L'illustration suivante représente la structure du dossier de publication pour un complément VSTO Outlook.  
  
     ![Structure du dossier de publication](../vsto/media/publishfolderstructure.png "Structure du dossier de publication")  
  
    > [!NOTE]  
    >  ClickOnce ajoute l'extension .deploy aux assemblys afin qu'une installation sécurisée d'Internet Information Services \(IIS\) ne bloque pas les fichiers en raison d'une extension non sécurisée.  Lorsque l'utilisateur installe la solution, ClickOnce supprime l'extension .deploy.  
  
14. Copiez les fichiers solution dans l'emplacement d'installation que vous avez spécifié précédemment dans cette procédure.  
  
##  <a name="Trust"></a> Déterminer comment accorder un niveau de confiance à la solution  
 Avant qu'une solution puisse s'exécuter sur les ordinateurs des utilisateurs, vous devez soit accorder votre confiance soit les utilisateurs doivent répondre à une invite d'approbation lorsqu'ils installent la solution.  Pour accorder un niveau de confiance à la solution, signez les manifestes à l'aide d'un certificat qui identifie un éditeur connu et approuvé.  Consultez [La confiance à la solution lors de la signature de l'application et les manifestes de déploiement](../vsto/granting-trust-to-office-solutions.md#Signing).  
  
 Si vous déployez une personnalisation au niveau du document et que vous souhaitez placer le document dans un dossier sur l'ordinateur de l'utilisateur ou rendre le document disponible sur un site SharePoint, assurez\-vous qu'Office approuve l'emplacement du document.  Consultez [Octroi de niveaux de confiance à des documents](../vsto/granting-trust-to-documents.md).  
  
##  <a name="Helping"></a> Aider les utilisateurs à installer la solution  
 Les utilisateurs peuvent installer la solution en exécutant le programme d'installation, en ouvrant le manifeste de déploiement, ou dans le cas d'une personnalisation au niveau du document, en ouvrant le document directement.  Il est recommandé que les utilisateurs installent votre solution à l'aide du programme d'installation.  Les deux autres approches ne garantissent pas que le logiciel requis soit installé.  Si les utilisateurs souhaitent ouvrir le document à partir de l'emplacement d'installation, ils doivent l'ajouter à la liste des emplacements approuvés dans le Centre de gestion de la confidentialité des applications Office.  
  
### Ouverture du document d'une personnalisation au niveau du document  
 Les utilisateurs peuvent ouvrir le document d'une personnalisation au niveau du document à partir de l'emplacement d'installation ou en copiant le document sur leur ordinateur local, puis en ouvrant la copie.  
  
 Il est recommandé que les utilisateurs ouvrent une copie du document sur leurs ordinateurs afin que plusieurs utilisateurs n'essayent pas d'ouvrir la même copie simultanément.  Pour mettre en œuvre ce principe, vous pouvez configurer votre programme d'installation pour copier le document sur les ordinateurs d'utilisateur.  Consultez [Placer le document d'une solution sur l'ordinateur de l'utilisateur final (personnalisations au niveau du document uniquement)](#Put).  
  
### Installation de la solution en ouvrant le manifeste de déploiement à partir d'un site Web IIS  
 Les utilisateurs peuvent installer une solution Office en ouvrant le manifeste de déploiement à partir du Web.  Toutefois, une installation sûre d'Internet Information Services \(IIS\) bloquera les fichiers portant l'extension .vsto.  Le type MIME doit être défini dans IIS avant de pouvoir déployer une solution Office à l'aide d'IIS.  
  
##### Pour ajouter le type MIME .vsto à IIS 6.0  
  
1.  Sur le serveur qui exécute IIS 6.0, choisissez **Démarrer**, pointez successivement sur **Tous les programmes** et **Outils d'administration**, puis  **Gestionnaire des services Internet \(IIS\)**.  
  
2.  Choisissez le nom de l'ordinateur, le dossier **Sites Web** ou le site Web que vous configurez.  
  
3.  Dans la barre de menus, choisissez **Action**, **Propriétés**.  
  
4.  Dans l'onglet **En\-têtes HTTP**, choisissez le bouton **Types MIME**.  
  
5.  Dans la fenêtre**Types MIME**, choisissez le bouton **Nouveau**.  
  
6.  Dans la fenêtre **Type MIME**, entrez **.vsto** comme extension, puis **application\/x\-ms\-vsto** comme type MIME, puis appliquez les nouveaux paramètres.  
  
    > [!NOTE]  
    >  Pour que les modifications soient prises en compte, vous devez redémarrer le service de publication World Wide Web ou attendre le recyclage du processus de travail.  Vous devez ensuite vider le cache disque du navigateur et essayer d'ouvrir à nouveau le fichier .vsto.  
  
##### Pour ajouter le type MIME .vsto à IIS 7.0  
  
1.  Sur le serveur qui exécute IIS 7.0, choisissez **Démarrer**, **Tous les programmes**, **Accessoires**.  
  
2.  Ouvrez le menu contextuel de l'**Invite de commandes**, puis choisissez **Exécuter en tant qu'administrateur**.  
  
3.  Dans la boîte de dialogue **Ouvrir**, entrez le chemin d'accès suivant, puis choisissez **OK**.  
  
    ```  
    %windir%\system32\inetsrv   
    ```  
  
4.  Entrez la commande suivante, puis appliquez les nouveaux paramètres.  
  
    ```  
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']  
    ```  
  
    > [!NOTE]  
    >  Pour que les modifications soient prises en compte, vous devez redémarrer le service de publication World Wide Web ou attendre le recyclage du processus de travail.  Vous devez ensuite vider le cache disque du navigateur et essayer d'ouvrir à nouveau le fichier .vsto.  
  
##  <a name="Put"></a> Placer le document d'une solution sur l'ordinateur de l'utilisateur final \(personnalisations au niveau du document uniquement\)  
 Vous pouvez copier le document de votre solution sur l'ordinateur de l'utilisateur final en créant une action de post\-déploiement.  De cette manière, l'utilisateur n'a pas à copier manuellement le document à partir de l'emplacement d'installation sur son ordinateur après l'installation de votre solution.  Vous devez créer une classe qui définit l'action de post\-déploiement, qui génère et publie la solution, qui modifie le manifeste de l'application, et qui signe à nouveau l'application et le manifeste de déploiement.  
  
 Les procédures suivantes supposent que le nom de votre projet soit **ExcelWorkbook** et que vous publiez la solution dans le répertoire **C:\\publish** de votre ordinateur.  
  
### Créer une classe qui définit l'action de post\-déploiement  
  
1.  Dans la barre de menus, cliquez sur **Fichier**, **Ajouter**, **Nouveau projet**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouveau projet**, dans le volet **Modèles installés**, choisissez le dossier **Windows**.  
  
3.  Dans le volet **Modèles**, choisissez le modèle **Bibliothèque de classes**.  
  
4.  Dans le champ **Nom**, entrez **FileCopyPDA**, puis choisissez le bouton **OK**.  
  
5.  Dans l'**Explorateur de solutions**, choisissez le projet **FileCopyPDA**.  
  
6.  Dans la barre de menus, choisissez **Projet**, **Ajouter une référence**.  
  
7.  Dans l'onglet **.NET**, ajoutez les références à Microsoft.VisualStudio.Tools.Applications.Runtime et Microsoft.VisualStudio.Tools.Applications.ServerDocument.  
  
8.  Remplacez le nom de la classe par `FileCopyPDA`, puis remplacez le contenu du fichier par le code.  Ce code exécute les tâches suivantes :  
  
    -   Il copie le document dans le bureau de l'utilisateur.  
  
    -   Remplace la propriété \_AssemblyLocation d'un chemin d'accès relatif en un chemin qualifié complet pour le manifeste de déploiement.  
  
    -   Il supprime le fichier si l'utilisateur désinstalle la solution.  
  
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../snippets/csharp/VS_Snippets_OfficeSP/trin_excelworkbookpda/cs/filecopypda/class1.cs#7)]
     [!code-vb[Trin_ExcelWorkbookPDA#7](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_excelworkbookpda/vb/filecopypda/class1.vb#7)]  
  
### Générer et publier la solution  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du projet**FileCopyPDA**, puis choisissez **Générer**.  
  
2.  Ouvrez le menu contextuel du projet **ExcelWorkbook**, puis choisissez **Générer**.  
  
3.  Ouvrez le menu contextuel du projet **ExcelWorkbook**, puis choisissez **Ajouter une référence**.  
  
4.  Dans la boîte de dialogue **Ajouter une référence**, choisissez l'onglet **Projets**, puis **FileCopyPDA** et cliquez sur le bouton **OK**.  
  
5.  Dans l'**Explorateur de solutions**, choisissez le projet **ExcelWorkbook**.  
  
6.  Dans la barre de menus, choisissez **Projet**, **Nouveau dossier**.  
  
7.  Entrez Données, puis appuyez sur la touche Entrée.  
  
8.  Dans l'**Explorateur de solutions**, choisissez le dossier **Données**.  
  
9. Dans la barre de menus, choisissez **Projet**, **Ajouter un élément existant**.  
  
10. Dans la boîte de dialogue **Ajouter un élément existant**, accédez au répertoire de sortie du projet **ExcelWorkbook**, choisissez le fichier **ExcelWorkbook.xlsx**, puis choisissez le bouton **Ajouter**.  
  
11. Dans l'**Explorateur de solutions**, choisissez le fichier **ExcelWorkbook.xlsx**.  
  
12. Dans la fenêtre **Propriétés**, remplacez la propriété **Action de génération** par **Contenu** et la propriété **Copier dans le répertoire de sortie** par **Copier si plus récent**.  
  
     Lorsque vous avez terminé ces étapes, votre projet ressemblera à l'illustration suivante.  
  
     ![Structure du projet de l'action post-déploiement.](../vsto/media/vsto-postdeployment.png "Structure du projet de l'action post-déploiement.")  
  
13. Publiez le projet **ExcelWorkbook**.  
  
### Modifier le manifeste d'application  
  
1.  Ouvrez le répertoire **C:\\publish** à l'aide de l'**Explorateur de fichiers**.  
  
2.  Ouvrez le dossier **Fichiers d'application**, puis ouvrez le dossier correspondant à la version publiée la plus récente de votre solution.  
  
3.  Ouvrez le fichier **ExcelWorkbook.dll.manifest** dans un éditeur de texte tel que le Bloc\-notes.  
  
4.  Ajoutez le code suivant après l'élément `</vstav3:update>`.  Pour l'attribut de classe de l'élément `<vstav3:entryPoint>`, utilisez la syntaxe suivante : *NomEspaceDeNoms.NomClasse*.  Dans l'exemple suivant, les noms de classe et l'espace de noms sont les mêmes, afin que le nom du point d'entrée résultant soit `FileCopyPDA.FileCopyPDA`.  
  
    ```  
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
  
### Signer à nouveau les manifestes d'application et de déploiement  
  
1.  Dans le dossier **%USERPROFILE%\\Documents\\Visual Studio 2013\\Projects\\ExcelWorkbook\\ExcelWorkbook**, copiez le fichier de certificat **ExcelWorkbook\_TemporaryKey.pfx** et collez\-le dans le dossier *DossierPublication***\\Fichiers Application\\ClasseurExcel***DernièreVersionPubliée*.  
  
2.  Ouvrez l'invite de commandes Visual Studio, puis remplacez les répertoires par le dossier **C:\\publish\\Fichiers Application\\ClasseurExcel***DernièreVersionPubliée* \(par exemple, **C:\\publish\\Fichiers Application\\ExcelWorkbook\_1\_0\_0\_4**\).  
  
3.  Signez le manifeste d'application modifié en exécutant la commande suivante :  
  
    ```  
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx  
    ```  
  
     Le message « ExcelWorkbook.dll.manifest signé avec succès » s'affiche.  
  
4.  Allez dans le dossier **C:\\publish**, puis mettez à jour et signez le manifeste de déploiement en exécutant la commande suivante :  
  
    ```  
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex  
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"  
    ```  
  
    > [!NOTE]  
    >  Dans l'exemple précédent, remplacez DernièreVersionPubliée par le numéro de version de la dernière version publiée de votre solution \(par exemple, **1\_0\_0\_4**\).  
  
     Le message « ExcelWorkbook.vsto signé avec succès » s'affiche.  
  
5.  Copiez le fichier ExcelWorkbook.vsto dans le répertoire **C:\\publish\\Fichiers Application\\ClasseurExcel***DernièreVersionPubliée*.  
  
##  <a name="SharePoint"></a> Placer le document d'une solution sur un serveur exécutant SharePoint \(personnalisations au niveau du document uniquement\)  
 Vous pouvez publier votre personnalisation au niveau du document pour les utilisateurs finaux à l'aide de SharePoint.  Lorsque les utilisateurs accèdent au site SharePoint et ouvrent le document, le runtime installe automatiquement la solution à partir du dossier réseau partagé sur l'ordinateur local de l'utilisateur.  Une fois que la solution est installée localement, la personnalisation fonctionne toujours même si le document est copié ailleurs, sur le bureau par exemple.  
  
#### Pour placer le document sur un serveur exécutant SharePoint  
  
1.  Ajoutez le document de solution à une bibliothèque de documents située sur un site SharePoint.  
  
2.  Suivez les étapes de l'une des méthodes suivantes :  
  
    -   Utilisez l'outil de configuration d'Office pour ajouter le serveur exécutant SharePoint au Centre de gestion de la confidentialité dans Word ou Excel sur tous les ordinateurs des utilisateurs.  
  
         Consultez [Stratégies et paramètres de sécurité dans Office 2010](http://go.microsoft.com/fwlink/?LinkId=99227).  
  
    -   Vérifiez que chaque utilisateur effectue les étapes suivantes.  
  
        1.  Sur l'ordinateur local, ouvrez Word ou Excel, choisissez l'onglet **Fichier**, puis le bouton **Options**.  
  
        2.  Dans la boîte de dialogue **Centre de gestion de la confidentialité**, choisissez le bouton **Emplacements approuvés**.  
  
        3.  Activez la case à cocher **Autoriser les emplacements approuvés sur mon réseau \(non recommandé\)**, puis choisissez le bouton **Ajouter un nouvel emplacement**.  
  
        4.  Dans la zone **Chemin d'accès**, entrez l'URL de la bibliothèque de documents SharePoint qui contient le document que vous avez téléchargé \(par exemple, *http:\/\/NomServeurSharePoint\/NomÉquipe\/NomProjet\/NomBibliothèqueDocuments*\).  
  
             N'ajoutez pas le nom de la page Web par défaut, par exemple default.aspx ou AllItems.aspx.  
  
        5.  Activez la case à cocher en regard de **Les sous\-dossiers de cet emplacement sont également approuvés**, puis choisissez le bouton **OK**.  
  
             Lorsque les utilisateurs ouvrent le document du site SharePoint, le document s'ouvre, et la personnalisation est installée.  Les utilisateurs peuvent copier le document sur leur bureau.  La personnalisation fonctionne toujours car les propriétés du document pointent vers l'emplacement réseau du document.  
  
##  <a name="Custom"></a> Créer un programme d'installation personnalisé  
 Vous pouvez créer un programme d'installation personnalisée pour votre solution Office, au lieu d'utiliser le programme d'installation qui est créé lorsque vous publiez la solution.  Par exemple, vous pouvez utiliser un script de connexion pour démarrer l'installation des solutions Office ou utiliser un fichier de commandes pour installer la solution Office sans intervention de l'utilisateur.  Ces scénarios conviennent parfaitement si les composants requis sont déjà installés sur les ordinateurs des utilisateurs finaux.  
  
 Dans le cadre du processus d'installation personnalisé, appelez le programme d'installation de solutions Office \(VSTOInstaller.exe\), qui est installé dans l'emplacement suivant par défaut :  
  
 %commonprogramfiles%\\microsoft shared\\VSTO\\10.0\\VSTOInstaller.exe  
  
 Si l'outil ne se trouve pas dans cet emplacement, vous pouvez également utiliser la clé de Registre HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VSTO Runtime Setup\\v4\\InstallerPath ou HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\VSTO Runtime Setup\\v4\\InstallerPath pour trouver le chemin d'accès vers cet outil.  
  
 Vous pouvez utiliser les paramètres suivants avec VSTOinstaller.exe.  
  
|Paramètre|Définition|  
|---------------|----------------|  
|\/Install ou \/I|Installe la solution.  Vous devez utiliser cette option avec le chemin d'accès d'un manifeste de déploiement.  Vous pouvez spécifier un chemin d'accès sur l'ordinateur local, un partage de fichiers UNC \(Universal Naming Convention\).  Vous pouvez spécifier un chemin local \(*C:\\NomDossier\\DossierPublication*\), un chemin relatif \(*Publication\\*\), ou un emplacement complet \(*\\\\NomServeur\\NomDossier* ou http:\/\/*NomServeur\/NomDossier*\).|  
|\/Uninstall ou \/U|Désinstalle la solution.  Vous devez utiliser cette option avec le chemin d'accès d'un manifeste de déploiement.  Vous pouvez spécifier qu'un chemin d'accès peut se trouver sur l'ordinateur local, un partage de fichiers UNC.  Vous pouvez spécifier un chemin local \(*C:\\NomDossier\\DossierPublication*\), un chemin relatif \(*Publication\\*\), ou un emplacement complet \(*\\\\NomServeur\\NomDossier* ou http:\/\/*NomServeur\/NomDossier*\).|  
|\/Silent ou \/S|Installez ou désinstallez sans inviter l'utilisateur à entrer de texte ni afficher de message.  Si une invite d'approbation est requise, la personnalisation n'est ni installée ni mise à jour.|  
|\/Help ou \/?|Affiche les informations d'aide.|  
  
 Lorsque vous exécutez VSTOinstaller.exe, les codes d'erreur suivants peuvent s'afficher.  
  
|Code d'erreur|Définition|  
|-------------------|----------------|  
|0|La solution a été installée ou désinstallée ou l'aide de VSTOInstaller s'est affichée.|  
|\-100|Une ou plusieurs options de ligne de commande ne sont pas valides ou ont été définies plusieurs fois.  Pour plus d'informations, entrez « vstoinstaller \/? » ou consultez [Création d'un programme d'installation personnalisé pour une solution Office ClickOnce](http://msdn.microsoft.com/fr-fr/3e5887ed-155f-485d-b8f6-3c02c074085e).|  
|\-101|Une ou plusieurs options de ligne de commande ne sont pas valides.  Pour plus d'informations, entrez « vstoinstaller \/? ».|  
|\-200|L'URI du manifeste de déploiement n'est pas valide.  Pour plus d'informations, entrez « vstoinstaller \/? ».|  
|\-201|La solution n'a pas pu être installée parce que le manifeste de déploiement n'est pas valide.  Consultez [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md).|  
|\-202|La solution n'a pas pu être installée parce que la section Visual Studio Tools pour Office du manifeste de l'application n'est pas valide.  Consultez [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).|  
|\-203|La solution n'a pas pu être installée suite à une erreur de téléchargement.  Vérifiez l'URI ou l'emplacement de fichier réseau du manifeste de déploiement et réessayez.|  
|\-300|La solution n'a pas pu être installée suite à une exception de sécurité.  Consultez [Sécurisation des solutions Office](../vsto/securing-office-solutions.md).|  
|\-400|La solution n'a pas pu être installée.|  
|\-401|La solution n'a pas pu être désinstallée.|  
|\-500|L'opération a été annulée parce que la solution n'a pas pu être installée et désinstallée ou le manifeste de déploiement ne peut pas être téléchargé.|  
  
##  <a name="Update"></a> Publier une mise à jour  
 Pour mettre à jour une solution, vous devez la publier à nouveau à l'aide du **Concepteur de projets** ou de l'**Assistant Publication**, puis copier la solution mise à jour dans l'emplacement d'installation.  Lorsque vous copiez les fichiers dans l'emplacement d'installation, assurez\-vous de remplacer les fichiers antérieurs.  
  
 La prochaine fois que la solution vérifiera la présence d'une mise à jour, elle recherchera et chargera automatiquement la nouvelle version.  
  
##  <a name="Location"></a> Modifier l'emplacement d'installation d'une solution  
 Vous pouvez ajouter ou modifier le chemin d'installation après avoir publié une solution.  Vous pourriez vouloir modifier le chemin d'installation pour l'une ou plusieurs des raisons suivantes :  
  
-   Le chemin d'installation n'était pas connu lors de la compilation du programme d'installation.  
  
-   Les fichiers solution ont été copiés vers un autre emplacement.  
  
-   Le serveur qui héberge les fichiers d'installation a un nouveau nom ou emplacement.  
  
 Pour modifier le chemin d'installation d'une solution, vous devez mettre à jour le programme d'installation, puis les utilisateurs doivent l'exécuter.  Pour les personnalisations au niveau du document, les utilisateurs doivent également mettre à jour une propriété dans le document pour afficher le nouvel emplacement.  
  
> [!NOTE]  
>  Si vous ne souhaitez pas demander aux utilisateurs de mettre à jour leurs propriétés de document, vous pouvez leur demander d'obtenir le document mis à jour de l'emplacement d'installation.  
  
#### Pour modifier le chemin d'installation dans le programme d'installation  
  
1.  Ouvrez une fenêtre **Invite de commandes**, puis accédez au répertoire du dossier d'installation.  
  
2.  Exécutez le programme d'installation et incluez le paramètre `/url`, qui prend le nouveau chemin d'installation comme une chaîne.  
  
     L'exemple suivant indique comment modifier le chemin d'installation dans un emplacement sur le site Web Fabrikam, mais vous pouvez remplacer cette URL par le chemin d'accès souhaité :  
  
    ```  
    setup.exe /url="http://www.fabrikam.com/newlocation"  
    ```  
  
    > [!NOTE]  
    >  Si un message apparaît et indique que la signature du fichier exécutable sera invalidée, le certificat utilisé pour signer la solution n'est plus valide, le serveur de publication est inconnu.  Par conséquent, les utilisateurs devront confirmer qu'ils font confiance à la source de la solution avant de pouvoir l'installer.  
  
    > [!NOTE]  
    >  Pour afficher la valeur actuelle de l'URL, exécutez `setup.exe /url`.  
  
 Pour les personnalisations au niveau du document, les utilisateurs doivent ouvrir le document puis mettre à jour la propriété \_AssemblyLocation.  Les étapes suivantes décrivent comment les utilisateurs peuvent effectuer cette tâche.  
  
#### Pour mettre à jour la propriété \_AssemblyLocation dans un document  
  
1.  Sous l'onglet **Fichier**, choisissez **Info**, comme indiqué dans l'illustration suivante.  
  
     ![Onglet Informations dans Excel](../vsto/media/vsto-infotab.png "Onglet Informations dans Excel")  
  
2.  Dans la liste **Propriétés**, choisissez **Propriétés avancées** comme indiqué dans l'illustration suivante.  
  
     ![Propriétés avancées dans Excel.](../vsto/media/vsto-advanceddocumentproperties.png "Propriétés avancées dans Excel.")  
  
3.  Dans l'onglet **Personnalisé** de la liste **Propriétés**, choisissez \_AssemblyLocation, comme indiqué dans l'illustration suivante.  
  
     ![Propriété AssemblyLocation.](../vsto/media/vsto-assemblylocationproperty.png "Propriété AssemblyLocation.")  
  
     La zone **Valeur** contient l'identificateur de manifeste de déploiement.  
  
4.  Avant l'identificateur, tapez le chemin d'accès qualifié complet du document, suivi d'une barre, selon le format *Chemin d'accès* |*Identificateur* \(par exemple, *File:\/\/NomServeur\/NomDossier\/NomFichier|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9*.  
  
     Pour plus d'informations sur la manière de mettre en forme cet identificateur, consultez [Vue d'ensemble des propriétés de document personnalisées](../vsto/custom-document-properties-overview.md).  
  
5.  Choisissez le bouton **OK**, puis enregistrez et fermez le document.  
  
6.  Exécutez le programme d'installation sans le paramètre \/url pour installer la solution à l'emplacement spécifié.  
  
##  <a name="Roll"></a> Restaurer la version antérieure d'une solution  
 Lorsque vous restaurez une solution, vous revenez à une version antérieure de cette solution.  
  
#### Pour restaurer une solution  
  
1.  Ouvrez l'emplacement d'installation de la solution.  
  
2.  Supprimez le manifeste de déploiement \(fichier .vsto\) qui se trouve dans le dossier de publication de niveau supérieur.  
  
3.  Recherchez le sous\-dossier de la version que vous souhaitez restaurer.  
  
4.  Copiez le manifeste de déploiement depuis ce sous\-dossier vers le dossier de publication de niveau supérieur.  
  
     Par exemple, pour passer de la version 1.0.0.1 d'une solution appelée **OutlookAddIn1** à la version 1.0.0.0, copiez le fichier **OutlookAddIn1.vsto** à partir du dossier **OutlookAddIn1\_1\_0\_0\_0**.  Collez le fichier dans le dossier de niveau supérieur, en remplaçant le manifeste de déploiement spécifique de la version **OutlookAddIn1\_1\_0\_0\_1** qui y était déjà.  
  
     L'illustration suivante représente la structure des dossiers de publication de cet exemple.  
  
     ![Structure du dossier de publication](../vsto/media/publishfolderstructure.png "Structure du dossier de publication")  
  
     Le changement de manifeste de déploiement sera détecté la prochaine fois qu'un utilisateur ouvre l'application ou le document personnalisé.  La version antérieure de la solution Office s'exécute depuis le cache ClickOnce.  
  
> [!NOTE]  
>  Les données locales ne sont enregistrées que pour la dernière version d'une solution.  Si vous restaurez l'avant dernière version et au\-delà, les données locales ne sont pas conservées.  Pour plus d'informations sur les données locales, consultez [Accessing Local and Remote Data in ClickOnce Applications](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## Voir aussi  
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)   
 [Publication de solutions Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Comment : publier une solution Office à l'aide de ClickOnce](http://msdn.microsoft.com/fr-fr/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Comment : installer une solution Office ClickOnce](http://msdn.microsoft.com/fr-fr/14702f48-9161-4190-994c-78211fe18065)   
 [Comment : publier une solution Office au niveau d'un document vers un serveur SharePoint à l'aide de ClickOnce](http://msdn.microsoft.com/fr-fr/2408e809-fb78-42a1-9152-00afa1522e58)   
 [Création d'un programme d'installation personnalisé pour une solution Office ClickOnce](http://msdn.microsoft.com/fr-fr/3e5887ed-155f-485d-b8f6-3c02c074085e)  
  
  