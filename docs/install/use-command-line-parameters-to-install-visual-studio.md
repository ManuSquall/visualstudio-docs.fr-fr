---
title: "Utiliser les paramètres de ligne de commande pour installer Visual Studio │ Microsoft Docs"
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: d4d1bd45ce697017480b3f63d0c7feb5ab20d2d6
ms.openlocfilehash: 18a3d03663ac96e0751d4a420244b835be7146bf
ms.lasthandoff: 02/22/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017-rc"></a>Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 RC
Quand vous installez Visual Studio 2017 RC à partir d’une invite de commandes, vous pouvez utiliser les paramètres de ligne de commande suivants (également appelés commutateurs).  

## <a name="list-of-command-line-parameters"></a>Liste des paramètres de ligne de commande  
 Les paramètres de ligne de commande Visual Studio ne respectent pas la casse.  

| **Commande de ligne de commande** | **Description** |
| ----------------------- | --------------- |  
| ```modify``` | Modifie un produit installé. |
| ```update``` | Met à jour un produit installé. |
| ```repair``` | Répare un produit installé. |
| ```uninstall``` | Désinstalle un produit installé. |

Si aucune commande n’est spécifiée, installe le produit.

| **Option de ligne de commande** | **Description** |
| ----------------------- | --------------- |  
| ```--installPath <dir>``` | Répertoire d’installation de l’instance à installer. Pour la commande d’installation, il s’agit de l’emplacement où l’instance doit être installée. Pour les autres commandes, il s’agit de l’emplacement où l’instance précédente à été installée. |
| ```--productId <id>``` | ID de produit pour l’instance à installer. Cette option est nécessaire pour la commande d’installation, ignorée pour les autres commandes si --installPath est spécifié. |
| ```--layout <dir>``` | Facultatif : Spécifie un répertoire pour créer un cache d’installation hors connexion. Cette option ajoute implicitement l’option '--wait'. |
| ```--lang <language-locale>``` *[&#60;paramètres régionaux de langue&#62; ...]* | Facultatif : Installer ou désinstaller des packages de ressources avec la ou les langues spécifiées. |
| ```--add <workload or component ID>``` *[&#60;ID de charge de travail ou composant&#62; ...]* | Facultatif : Un ou plusieurs ID de charge de travail ou composant à ajouter. Les composants obligatoires de l’artefact sont installés, mais pas les composants recommandés ni facultatifs. Vous pouvez contrôler globalement les autres composants à l’aide des options '--includeRecommended' et/ou '--includeOptional'. Pour un contrôle plus précis, vous pouvez ajouter ';includeRecommended' et/ou ';includeOptional' à l’artifactId (par exemple, '--add Workload1;includeRecommended' ou '--add Workload2;includeOptional;includeRecommended'). |
| ```--remove <workload or component ID>``` *[&#60;ID de charge de travail ou composant&#62; ...]* | Facultatif : Un ou plusieurs ID de charge de travail ou composant à supprimer. |
| ```--all``` | Facultatif : Indique s’il faut installer tous les composants et charges de travail d’un produit. |
| ```--allWorkloads``` | Facultatif : Installe toutes les charges de travail et leurs composants obligatoires, mais n’installe pas les composants recommandés et facultatifs. |
| ```--includeRecommended``` | Facultatif : Inclut les composants recommandés pour toutes les charges de travail installées, mais pas les composants facultatifs. Les charges de travail sont spécifiées avec --allWorkloads ou --add. |
| ```--includeOptional``` | Facultatif : Inclut les composants facultatifs pour toutes les charges de travail installées, mais pas les composants recommandés. Les charges de travail sont spécifiées avec --allWorkloads ou --add.  |
| ```--quiet, -q``` | Facultatif : Ne pas afficher l’interface utilisateur pendant l’installation. |
| ```--passive, -p``` | Facultatif : Afficher l’interface utilisateur, mais ne pas demander d’intervention de l’utilisateur. |
| ```--norestart``` | Facultatif : Les commandes avec --passive ou --quiet ne redémarrent pas automatiquement l’ordinateur (si nécessaire). Option ignorée si --passif et --quiet ne sont pas spécifiés.  |
| ```--locale <language-locale>``` | Facultatif : Modifier la langue d’affichage de l’interface utilisateur pour le programme d’installation. Ce paramètre est conservé. |
| ```--nickname <name>``` | Facultatif : Définit le surnom à attribuer à un produit installé. La longueur du surnom ne peut pas dépasser 10 caractères.  |
| ```--help, --?, -h, -?``` | Afficher l’utilisation des paramètres. |

>Remarque : Lorsque vous spécifiez plusieurs charges de travail et plusieurs composants, vous devez répéter le commutateur de ligne de commande `--add` ou `--remove` pour chaque élément.

| **Option de ligne de commande avancée** | **Description** |
| ----------------------- | --------------- |  
| ```--channelId <id>``` | Facultatif : ID de canal pour l’instance à installer. Cette option est nécessaire pour la commande d’installation, ignorée pour les autres commandes si --installPath est spécifié. |
| ```--channelUri <uri>``` | Facultatif : URI du manifeste de canal. Cette option peut être utilisée pour la commande d’installation. Elle est ignorée pour les autres commandes. |
| ```--installChannelUri <uri>``` | Facultatif : URI du manifeste de canal à utiliser pour l’installation. L’URI spécifié par --channelUri (qui doit être spécifié en même temps que --installChannelUri) est utilisé pour détecter les mises à jour. Si les mises à jour ne sont pas souhaitées, vous devez spécifier --channelUri sans argument. Cette option peut être utilisée pour la commande d’installation. Elle est ignorée pour les autres commandes. |
| ```--installCatalogUri <uri>``` | Facultatif : URI du manifeste de catalogue à utiliser pour l’installation. Si spécifié, le gestionnaire de canal va tenter de télécharger le manifeste de catalogue à partir de cet URI avant d’utiliser l’URI du manifeste de canal d’installation. Ce paramètre est utilisé pour prendre en charge l’installation hors connexion, où le cache de disposition est créé avec le catalogue de produits déjà téléchargé. Cette option peut être utilisée pour la commande d’installation. Elle est ignorée pour les autres commandes. |
| ```--in <path>``` | Facultatif : URI ou chemin d’un fichier réponse.  |
| ```--addProductLang <language-locale>``` | Facultatif : Définit la langue d’un artefact (groupe, charge de travail ou composant) à installer. Cette option peut apparaître plusieurs fois sur la ligne de commande. Elle est facultative pour installer et modifier des commandes, ignorée pour mettre à jour, réparer et désinstaller des commandes. Si elle est absente, l’installation utilise les paramètres régionaux de l’ordinateur. |
| ```--removeProductLang <language-locale>``` | Facultatif : Définit la langue d’un artefact (groupe, charge de travail ou composant) à supprimer. Cette option peut apparaître plusieurs fois sur la ligne de commande. Elle est facultative pour installer et modifier des commandes, ignorée pour mettre à jour, réparer et désinstaller des commandes. |
| ```--wait``` | Facultatif : Le processus attend la fin de l’installation pour retourner du code de sortie. Cela est utile lorsque vous automatisez des installations et que vous devez attendre la fin de l’installation pour gérer le code de retour de cette installation. |
| ```--productKey``` | Facultatif : Définit la clé de produit à utiliser pour un produit installé. Elle est composée de 25 caractères alphanumériques au format 'xxxxx-xxxxx-xxxxx-xxxxx-xxxxx' ou 'xxxxxxxxxxxxxxxxxxxxxxxxx'. |
## <a name="list-of-workload-ids-and-component-ids"></a>Liste des ID de charge de travail et de composant
Pour obtenir la liste des ID de charge de travail et de composant triés par produit Visual Studio, consultez notre page [ID de composant et de charge de travail Visual Studio 2017](https://aka.ms/vs2017componentids).

> [!WARNING]
> Le paramètre --layout échoue si le nom du fichier .exe d’installation comprend des chiffres. Pour contourner ce problème, vous devez supprimer les chiffres du nom du fichier, par exemple, renommez *vs_community__198521760.1486960229.exe* en ***vs_community.exe***.

## <a name="list-of-language-locales"></a>Liste des paramètres régionaux de langue
| **Paramètres régionaux de langue** | **Langue** |
| ----------------------- | --------------- |  
| cs-CZ | Tchèque |
| de-DE | Allemand |
| fr-FR | Anglais |
| es-ES | Espagnol |
| cs-CZ | Tchèque |
| fr-FR | Français |
| it-IT | Italien |
| ja-JP | Japonais |
| ko-KR | Coréen |
| pl-PL | Polonais |
| pt-BR | Portugais - Brésil |
| ru-RU | Russe |
| tr-TR | Turc |
| zh-CN | Chinois (simplifié) |
| zh-TW | Chinois (traditionnel) |



> [!IMPORTANT]
> Alors que Visual Studio 2017 RC est généralement pris en charge pour une utilisation dans un environnement de production, les charges de travail et les composants qui sont marqués « Préversion » dans l’interface utilisateur de l’installation ne le sont pas.

## <a name="see-also"></a>Voir aussi

 * [Installer Visual Studio](install-visual-studio.md)
 * [Créer une installation hors connexion de Visual Studio 2017 RC](create-an-offline-installation-of-visual-studio.md)
 * [Signaler un problème avec Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

