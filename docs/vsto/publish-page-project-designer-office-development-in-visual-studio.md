---
title: "Page Publier, Project Designer (développement Office dans Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
ms.assetid: 94d9bdf1-84fa-4e26-8ece-a1a0dabda5ea
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5ce726d9d86bd57e5cf245010212545f0055c8ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Page Publier, Concepteur de projets (Développement Office dans Visual Studio)
  La page **Publier** du **Concepteur de projets** permet de configurer les propriétés du déploiement.  
  
 Pour accéder à cette page, sélectionnez le projet dans **l’Explorateur de solutions**, puis, dans le **projet** menu, choisissez *nom_projet* **propriétés** . Si la page **Publier** n’apparaît pas, choisissez l’onglet **Publier** .  
  
> [!NOTE]  
>  Vous pouvez également définir l’emplacement de publication dans l’ **Assistant Publication**. Pour plus d’informations, consultez [Comment : publier une solution Office à l’aide de ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).  
  
## <a name="uielement-list"></a>Liste UIElement  
 **Emplacement du dossier de publication (site web, serveur ftp ou chemin du fichier)**  
 Obligatoire.  
  
 L’emplacement du dossier de publication est le répertoire dans lequel Visual Studio copie les fichiers solution tels que les manifestes, les assemblys et les autres fichiers de la build. Vous devez disposer d’un accès en écriture à ce répertoire.  
  
 Les options incluent l’ordinateur local, un partage de fichiers UNC ou un site web HTTP/HTTPS. Le chemin d’accès peut être local (*c:\foldername\publishfolder*), relatif (*publier\\*), ou un emplacement qualifié complet (*\\\servername\foldername* ou http://*nomserveur/nomdossier*).  
  
 Par défaut, l’emplacement de publication est *http://localhost/nom_projet/* si IIS est installé, ou le répertoire publish\ si IIS n’est pas installé.  
  
 **URL du dossier d'installation**  
 Facultatif.  
  
 L’URL du dossier d’installation est le répertoire à partir duquel l’utilisateur final installe la personnalisation. Il s’agit également du chemin que la solution utilise pour vérifier les mises à jour. Le chemin peut être identique à l’emplacement du dossier de publication, mais cela n’est pas obligatoire.  
  
 Les options incluent l’ordinateur local, un partage de fichiers UNC ou un site web HTTP/HTTPS. Le chemin d’accès peut être local (*c:\foldername\publishfolder*), relatif (*publier\\*), ou un emplacement qualifié complet (*\\\servername\foldername* ou http://*nomserveur/nomdossier*). Tous les emplacements HTTP/HTTPS doivent être créés avec des caractères US-ASCII. Les caractères Unicode ne sont pas pris en charge.  
  
 Si le chemin d’installation est défini, les fichiers de personnalisation doivent se trouver à cet emplacement pour que les utilisateurs puissent installer la personnalisation. L’emplacement doit être défini uniquement si vous connaissez l’emplacement de déploiement final.  
  
 Si les fichiers d’installation se trouvent dans un emplacement relatif au document ou au programme d’installation, comme c’est le cas avec l’option CD, laissez cette zone vide.  
  
 Cette valeur peut être assignée plus tard par un administrateur. Pour plus d’informations, consultez [Comment : changer le chemin d’installation d’une solution Office](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 **Composants requis**  
 Les composants nécessaires peuvent être inclus dans le programme d’installation ou téléchargés à la demande durant l’installation.  
  
-   **Télécharger les composants requis à partir du site web du fournisseur de composants**: utilisez cette option pour télécharger les composants nécessaires à partir du site de Microsoft.  
  
-   **Télécharger les composants requis à partir de l’emplacement de mon application**: utilisez cette option pour créer un package des composants nécessaires dans votre programme d’installation. Si vous ajoutez les fichiers de composants nécessaires au programme d’installation, cela entraîne une augmentation de la taille de la solution.  
  
-   **Télécharger les composants requis depuis l’emplacement suivant**: utilisez cette option pour permettre à l’utilisateur final de disposer des composants nécessaires séparément via un autre programme d’installation situé sur une page web ou un partage réseau.  
  
 **Mises à jour**  
 L’intervalle de mise à jour détermine la fréquence à laquelle la solution vérifie l’existence de mises à jour. La valeur par défaut consiste à effectuer une vérification tous les sept jours.  
  
 La vérification des mises à jour à chaque chargement d’une personnalisation au niveau du document ou d’un complément VSTO contribue à son actualisation. Toutefois, cela affecte les performances de démarrage.  
  
 Si vous effectuez un déploiement à l’aide d’un CD ou d’un lecteur amovible, choisissez **Ne jamais vérifier**.  
  
 **Options (Description)**  
 Vous pouvez définir les options de publication des propriétés suivantes :  
  
-   Langue de publication : paramètres régionaux de la solution Office.  
  
-   Nom de l’éditeur : nom de la société ou du développeur, tel qu’il apparaît dans **Ajout/Suppression de programmes** ou **Programmes et fonctionnalités**.  
  
-   Nom du produit : nom de la solution Office, tel qu’il apparaît dans **Ajout/Suppression de programmes** ou **Programmes et fonctionnalités**.  
  
-   URL du support technique : adresse qui permet à l’utilisateur final de contacter le support technique de la solution Office.  
  
 **Options (Paramètres Office)**  
 Vous pouvez définir les options de publication des propriétés suivantes :  
  
-   Nom de solution : nom de la solution Office, tel qu’il apparaît dans l’application Office.  
  
-   Description : description de la solution Office, telle qu’elle apparaît dans l’application Office.  
  
-   Comportement de chargement du complément VSTO.  
  
    -   Charger au démarrage : indique que le complément VSTO est chargé au démarrage de l’application Office.  
  
    -   Charger à la demande : le complément VSTO est chargé uniquement quand l’application le nécessite, par exemple quand un utilisateur clique sur un élément d’interface utilisateur qui utilise une fonctionnalité du complément VSTO.  
  
 **Langue de publication**  
 Cette option définit la langue des termes du contrat de licence logiciel Microsoft, et inclut les modules linguistiques dans la liste des composants nécessaires. Elle n’affecte pas la langue de la personnalisation. La langue du programme d’installation est déterminée par les langues installées de Visual Studio.  
  
 Pour plus d’informations sur la façon de changer la **langue de publication**, consultez [How to: Change the Publish Language for a ClickOnce Application](/visualstudio/deployment/how-to-change-the-publish-language-for-a-clickonce-application).  
  
 **Version de publication**  
 Définit le numéro de version de la personnalisation. Quand vous changez le numéro de version, l’application est publiée en tant que mise à jour. Un dossier est créé pour chaque version pendant le processus de génération pour éviter de remplacer la version précédemment publiée. Chaque partie de la version de publication (**Majeure**, **Mineure**, **Build**, **Révision**) peut contenir jusqu’à 5 chiffres.  
  
 **Incrémenter automatiquement la révision avec chaque mise en production**  
 Facultatif. Quand cette option est sélectionnée (par défaut), la partie **Révision** du numéro de version est incrémentée d’une unité chaque fois que la personnalisation est publiée. Cela entraîne la publication de la personnalisation en tant que mise à jour.  
  
 **Publier maintenant**  
 Publie l’application à l’aide des paramètres actuels. Équivaut au bouton **Terminer** situé dans l’ **Assistant Publication**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md)   
 [Déploiement d’une Solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Composants requis de solutions Office pour le déploiement](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e)  
  
  