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
ms.openlocfilehash: 4f5b8e2d65454d75c08d3efc26af2fd93b22153b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284800"
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
   > Sur le site Web de la communauté des développeurs, il existe une limite de 2 Go sur les fichiers joints et un maximum de 10 fichiers. Si vous devez charger un fichier plus volumineux, vous pouvez envoyer un nouveau rapport de problème ou demander une URL de chargement à un employé de Microsoft dans un commentaire privé.
   > Lorsque nous fermons un problème, les pièces jointes associées seront supprimées après 90 jours.

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
> Les fichiers journaux, les captures d’écran et les données d’enregistrement que vous envoyez peuvent accroître considérablement la capacité de Microsoft à comprendre et à résoudre votre problème.  Nous vous recommandons donc de les inclure. Pour protéger votre confidentialité, les fichiers journaux, captures d’écran et données d’enregistrement joints sont envoyés uniquement à Microsoft lorsque vous fournissez une autorisation en soumettant le rapport de problème avec lequel ils sont inclus. Vous pouvez voir quels fichiers sont inclus dans l’étape « Résumé » de la fenêtre « signaler un problème » avant d’envoyer le rapport. Vous pouvez exclure des fichiers journaux système du rapport en désactivent l’option « joindre les journaux système » dans l’étape « Résumé ». Pour référence, consultez la capture d’écran suivante. 
  > ![Signaler un problème-Résumé des journaux collectés](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Voir aussi

- [Guide pratique pour signaler un problème avec Visual Studio](how-to-report-a-problem-with-visual-studio.md)
- [Confidentialité des données de rapport de problème C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
