---
title: 'Comment : gérer des fichiers de données locaux dans votre projet | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.data.LocalConnectionConverter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- mdf files
- local data
- .mdb files
- .mdf files
- data [Visual Studio], local
- mdb files
ms.assetid: 3ffa1aa9-17e4-422c-a02f-09224828cdfc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 16e2d38dda97bd8a7f130254b2f23be9f17e0ac4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271373"
---
# <a name="how-to-manage-local-data-files-in-your-project"></a>Comment : gérer des fichiers de données locaux dans votre projet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un fichier de base de données locale peut être inclus en tant que fichier dans un projet. La première fois que vous vous connectez à un fichier de base de données locale, vous pouvez choisir créer une copie dans votre projet ou vous connecter au fichier existant dans son emplacement actuel. Si vous vous connectez au fichier existant, il reste dans son emplacement d’origine. Si vous choisissez de copier le fichier dans votre projet, Visual Studio crée une copie de celle-ci, l’ajoute à votre projet et modifie la connexion pour pointer vers la copie. Autres connexions, telles que celles dans l’Explorateur de serveurs sont également modifiées.  
  
 Le paramètre par défaut de la propriété varie selon le type de fichier de base de données que vous utilisez. Le comportement de la **Copy to Output Directory** propriété ne s’applique pas aux projets Web ou C++.  
  
 Pendant le développement, vous souhaiterez peut-être afficher les effets de votre code sur la base de données sans apporter ces modifications permanentes. Vous pouvez le faire par le paramètre de la **Copy to Output Directory** propriété du fichier à la valeur true. Chaque fois que le projet est généré ou que vous appuyez sur F5, le fichier est copié dans le dossier bin et les modifications sont apportées à ce fichier, pas dans le fichier dans le dossier racine de votre projet. Le fichier de base de données dans votre dossier projet racine est modifié uniquement lorsque vous modifiez le schéma de base de données ou les données à l’aide de **Explorateur de serveurs**, **Database Explorer** ou autre fenêtre outil.  
  
 Le tableau suivant décrit les paramètres de la **Copy to Output Directory** propriété.  
  
|Paramètre|Comportement|  
|-------------|--------------|  
|**Copier si plus récent** (valeur par défaut pour les fichiers .sdf)|Le fichier de base de données est copié à partir du répertoire de projet pour le **bin** répertoire la première fois le projet est généré. Chaque fois suivante, vous générez le projet, le **Date de modification** propriété des fichiers est comparée. Si le fichier dans le dossier du projet est plus récent, il est copié dans le **bin** dossier, en remplaçant le fichier qui s’y trouve. Si le fichier dans le **bin** dossier est plus récent, aucun fichier n’est copiés. Ce paramètre conserve toutes les modifications apportées aux données pendant l’exécution, ce qui signifie que chaque fois que vous exécutez votre application et enregistrez les modifications apportées aux données, ces modifications sont visibles lors de la prochaine exécution de votre application. **Attention :** nous ne recommandons pas cette option pour les fichiers .mdb ou .mdf. Le fichier de base de données peut changer même si aucune modifications ne sont apportées aux données. Simple ouverture d’une connexion sur un fichier de données (par exemple, en développant le **Tables** nœud **Explorateur de serveurs**) pouvez le marquer comme étant plus récent.|  
|**Toujours copier** (valeur par défaut pour les fichiers .mdf et .mdb)|Le fichier de base de données est copié à partir du répertoire de projet dans le répertoire "/ bin" chaque fois que vous générez votre application. Par conséquent, si vous générez votre application et enregistrez les modifications dans le fichier dans le répertoire "/ bin", ces modifications sont remplacées la prochaine fois que le fichier d’origine est copié dans le répertoire /bin.|  
|**Ne pas copier**|Le fichier n’est jamais copié ni remplacé par le système de projet. Vous devez copier manuellement le fichier à partir du répertoire de projet dans le répertoire de sortie si vous utilisez ce paramètre.|  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-respond-to-the-local-database-file-dialog-box"></a>Pour répondre à la boîte de dialogue de fichier de base de données locale  
  
-   Cliquez sur **Oui** si vous souhaitez que Visual Studio pour copier le fichier de base de données dans votre projet et modifier la connexion pour pointer vers la copie dans votre projet. Pour plus d’informations sur l’utilisation des fichiers de base de données dans votre projet, consultez [vue d’ensemble des données locales](../data-tools/local-data-overview.md).  
  
-   Cliquez sur **non** si vous ne souhaitez pas que Visual Studio copie le fichier de base de données dans votre projet. Au lieu de cela, la connexion pointe vers le fichier dans l’emplacement d’origine et le fichier de base de données n’est pas ajouté au projet sous forme de fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Connexion aux données dans un fichier de base de données locale (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Se connecter à des données dans une base de données Access (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)