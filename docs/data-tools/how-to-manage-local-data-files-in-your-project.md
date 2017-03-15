---
title: "Comment&#160;: g&#233;rer des fichiers de donn&#233;es locaux dans votre projet | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.data.LocalConnectionConverter"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "fichiers .mdb"
  - "fichiers .mdf"
  - "données (Visual Studio), locaux"
  - "données locales"
  - "fichiers mdb"
  - "fichiers mdf"
ms.assetid: 3ffa1aa9-17e4-422c-a02f-09224828cdfc
caps.latest.revision: 29
caps.handback.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Comment&#160;: g&#233;rer des fichiers de donn&#233;es locaux dans votre projet
Un fichier de base de données local peut être inclus en tant que fichier dans un projet.  La première fois que vous connectez votre application à un fichier de base de données local, vous pouvez choisir entre créer une copie de la base de données dans votre projet ou vous connecter au fichier de base de données existant à son emplacement actuel.  Si vous choisissez de vous connecter au fichier existant, une connexion est créée, exactement comme dans le cas d'une base de données distante. Le fichier de base de données reste à son emplacement d'origine.  Si vous choisissez de copier la base de données dans votre projet, Visual Studio crée une copie du fichier de base de données, l'ajoute à votre projet et modifie la connexion afin qu'elle pointe vers la base de données de votre projet plutôt que vers l'emplacement d'origine du fichier de base de données.  
  
> [!NOTE]
>  Les connexions de données existantes présentes dans l'**Explorateur de serveurs\/bases de données** sont modifiées pour pointer également vers le fichier de base de données du projet \(le fichier de base de données qui se trouve dans le dossier racine du projet\).  
  
 Lorsque vous générez un projet, le fichier de base de données peut être copié du dossier racine du projet vers le dossier de sortie \(**bin**\). \(Sélectionnez **Afficher tous les fichiers** dans l'**Explorateur de solutions** pour afficher le dossier **bin**.\) Ce comportement dépend du paramétrage de la propriété **Copier dans le répertoire de sortie** du fichier.  Le paramètre par défaut de la propriété dépend du type de fichier de base de données que vous utilisez.  
  
> [!NOTE]
>  Le comportement de la propriété **Copier dans le répertoire de sortie** ne s'applique pas aux projets Web ou C\+\+.  
  
 Au cours du développement d'applications, toute modification apportée aux données \(au moment de l'exécution au sein de votre application\) est répercutée dans la base de données, dans le dossier **bin**.  Par exemple, lorsque vous appuyez sur F5 pour déboguer votre application, vous êtes connecté à la base de données qui se trouve dans le dossier **bin**.  Le fichier de base de données présent dans votre dossier projet racine est modifié uniquement lorsque vous modifiez le schéma ou les données de la base de données à l'aide de l'**Explorateur de serveurs**, **Explorateur de bases de données** ou d'autres [Visual Database Tools](http://msdn.microsoft.com/fr-fr/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Le tableau suivant décrit les paramètres de la propriété **Copier dans le répertoire de sortie**.  
  
|Paramètre|Comportement|  
|---------------|------------------|  
|**Copier si plus récent**  \(valeur par défaut pour les fichiers .sdf\)|Le fichier de base de données est copié du répertoire du projet dans le répertoire **bin** lors de la première génération du projet.  Par la suite, à chaque fois que vous générez le projet, la propriété **Date de modification** des fichiers fait l'objet d'une comparaison.  Si le fichier présent dans le dossier du projet est plus récent, il est copié dans le dossier **bin**, remplaçant ainsi le fichier qui s'y trouve.  Si le fichier présent dans le dossier **bin** est plus récent, aucun fichier n'est copié.  Ce paramètre conserve toutes les modifications apportées aux données au moment de l'exécution. En d'autres termes, à chaque fois que vous exécutez votre application et enregistrez les modifications apportées aux données, ces modifications sont visibles lors de l'exécution suivante de l'application. **Caution:**  Nous ne recommandons pas cette option pour les fichiers .mdb ou .mdf.  Le fichier de base de données peut changer même si aucune modification n'est apportée aux données.  La simple ouverture d'une connexion sur un fichier de données \(par exemple, en développant le nœud **Tables** dans l'**Explorateur de serveurs**\) peut marquer celui\-ci comme étant plus récent.|  
|**Toujours copier** \(valeur par défaut pour les fichiers .mdf et .mdb\)|Le fichier de base de données est copié du répertoire de projet vers le répertoire \/bin à chaque fois que vous générez votre application.  Par conséquent, si vous générez votre application et enregistrez des modifications dans le fichier du répertoire \/bin, ces modifications sont remplacées lors de la prochaine copie du fichier d'origine dans le répertoire \/bin.|  
|**Ne pas copier**|Le fichier n'est jamais copié ni remplacé par le système de projet.  Vous devez copier manuellement le fichier du répertoire du projet dans le répertoire de sortie si vous utilisez ce paramètre.|  
  
## Procédure  
  
#### Pour répondre à la boîte de dialogue Fichier de base de données local  
  
-   Cliquez sur **Oui** si vous souhaitez que Visual Studio copie le fichier de base de données dans votre projet et modifie la connexion de sorte qu'elle pointe sur cette copie.  Pour plus d'informations sur l'exploitation des fichiers de base de données dans votre projet, consultez [Vue d'ensemble des données locales](../data-tools/local-data-overview.md).  
  
-   Cliquez sur **Non** si vous ne souhaitez pas que Visual Studio copie le fichier de base de données dans votre projet.  Dans ce cas, la connexion pointe vers le fichier à l'emplacement d'origine et le fichier de base de données n'est pas ajouté au projet en tant que fichier.  
  
## Voir aussi  
 [Procédure pas à pas : connexion à des données dans un fichier de base de données local \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)   
 [Procédure pas à pas : connexion à des données dans une base de données Access \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)