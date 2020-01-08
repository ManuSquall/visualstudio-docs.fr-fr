---
title: Données privées pour les rapports de problème
ms.date: 06/21/2018
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09f3e5fed93cac3a251e4b7cdcaa988e63ff8741
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596266"
---
# <a name="developer-community-data-privacy"></a>Confidentialité des données de la communauté des développeurs

Par défaut, tout le monde peut voir la totalité des informations des rapports de problème dans la [Communauté des développeurs](https://developercommunity.visualstudio.com/), notamment les commentaires et les réponses. C’est un avantage parce qu’il permet à toute la communauté d’avoir accès aux problèmes, solutions et solutions de contournement trouvés par d’autres utilisateurs. Toutefois, si vous êtes inquiet concernant la confidentialité de vos données ou de votre identité, plusieurs options s’offrent à vous.

## <a name="identity-privacy"></a>Confidentialité de l’identité

Si vous ne souhaitez pas révéler votre identité, [créez un compte Microsoft](https://signup.live.com/) qui ne divulgue aucun détail vous concernant. Utilisez ce compte pour créer votre rapport.

## <a name="data-privacy"></a>Confidentialité des données

Si vous êtes soucieux de la confidentialité des données, ne placez pas d’informations privées dans le titre ou le contenu du rapport initial, qui est toujours public. Au lieu de cela, créez le rapport, puis envoyez des détails en privé dans un commentaire séparé. Une fois le rapport de problème créé, vous pouvez spécifier qui peut voir vos réponses et pièces jointes :

1. Dans le rapport que vous avez créé, choisissez **Ajouter un commentaire** pour créer une description privée du problème.

2. Dans l’éditeur de réponse, utilisez la commande sous les boutons **Envoyer** et **Annuler** pour spécifier l’audience de votre réponse. Choisissez **Viewable by moderators and the original poster** (Consultable par les modérateurs et l’auteur à l’origine de la publication) pour limiter la visibilité aux employés de Microsoft et à vous-même.

   ![Contrôle de confidentialité dans la Communauté des développeurs](media/developer-community-privacy-control.png)

   Seules les personnes que vous spécifiez peuvent voir le commentaire et les images, liens ou extraits de code que vous incluez. Toutes les réponses sous le commentaire ont la même visibilité que le commentaire d’origine. Cela est vrai même si le contrôle de confidentialité sur les réponses n’affiche pas correctement l’état de visibilité restreinte.

3. Ajoutez la description et les autres informations, images et pièces jointes de fichier nécessaires à la reproduction. Choisissez le bouton **Envoyer** pour envoyer ces informations en privé.

   > [!NOTE]
   > Les fichiers joints sont limités à 10 et ils ne doivent pas dépasser 2 Go. Si vous devez charger un fichier plus volumineux, vous pouvez envoyer un nouveau rapport de problème ou demander une URL de chargement à un employé de Microsoft dans un commentaire privé.

Pour assurer votre confidentialité et ne pas dévoiler d’informations sensibles au public, veillez à limiter toutes les interactions avec Microsoft aux réponses sous un commentaire à visibilité restreinte. Le fait de répondre à d’autres commentaires peut vous amener à divulguer accidentellement des informations sensibles.

## <a name="data-we-collect"></a>Données que nous collectons

Si **Signaler un problème** est lancé à partir de Visual Studio Installer, nous collectons le journal d’installation le plus récent.

Si **Signaler un problème** est lancé à partir de Visual Studio, nous collectons un ou plusieurs des types de données suivants :

- Entrées Watson et .NET du journal des événements

- Fichier journal des activités en mémoire de Visual Studio

- Fichiers PerfWatson, si la collection Watson est activée

- Fichiers journaux LiveShare, s’ils existent

- Fichiers journaux Xamarin, s’ils existent

- Fichiers journaux Nuget, s’ils existent

- Fichiers journaux du débogueur web, s’ils existent

- Journaux Service Hub et journaux d’erreurs MEF, s’ils existent

- Journaux Python, s’ils existent

- Windows Forms les journaux, s’ils existent

- Une capture d’écran, si vous choisissez de l’inclure

- Les données d’enregistrement, si vous choisissez d’inclure un enregistrement, qui comprennent :

  - Les étapes pour reproduire le problème.

  - Le fichier de trace ETL.

  - Le fichier dump.

> [!NOTE]
> Les fichiers journaux, les captures d’écran et les données d’enregistrement sont envoyés à Microsoft uniquement lorsque vous fournissez une autorisation en soumettant le rapport de problème avec lequel ils sont inclus. Vous pouvez voir quels fichiers sont inclus dans l’étape « Résumé » de la fenêtre « signaler un problème » (voir la capture d’écran incluse dans cette note). Les journaux et les fichiers collectés sont stockés dans le dossier% Temp% et sont nettoyés régulièrement et après chaque téléchargement. Si vous ne souhaitez pas inclure de journal dans votre rapport de problème, supprimez le fichier du dossier% Temp% avant d’envoyer le rapport.
  > ![signaler un problème-Résumé des journaux collectés](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Voir aussi

- [Comment signaler un problème avec Visual Studio](how-to-report-a-problem-with-visual-studio.md)
- [Confidentialité des données de rapport de problème C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
