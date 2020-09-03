---
title: Récupération automatique, Environnement, boîte de dialogue Options | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 743543e03806a842eabc2bbfc69011d63b1264d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660976"
---
# <a name="autorecover-environment-options-dialog-box"></a>Récupération automatique, Environnement, boîte de dialogue Options
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez cette page de la boîte de dialogue Options pour spécifier si les fichiers sont automatiquement sauvegardés ou non. Cette page vous permet également de spécifier si les fichiers modifiés sont restaurés ou non quand l’environnement de développement intégré (IDE) s’arrête de façon inattendue. Vous pouvez accéder à cette boîte de dialogue en sélectionnant **Options** dans le menu **Outils**, puis la page **Récupération automatique** dans le dossier **Environnement**. Si cette page n’apparaît pas dans la liste, sélectionnez **Afficher tous les paramètres** dans la boîte de dialogue **Options**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **Enregistrer les informations de récupération automatique toutes les \<n> minutes** Utilisez cette option pour personnaliser la fréquence d’enregistrement automatique d’un fichier dans l’éditeur. Pour les fichiers précédemment enregistrés, une copie du fichier est enregistrée dans \\ . ..\Mes documents\Visual Studio \<*version*> \Sauvegarde fichiers \\ < *ProjectName*>. Si le fichier est nouveau et n’a pas été enregistré manuellement, le fichier est enregistré automatiquement à l’aide d’un nom de fichier généré de manière aléatoire.

 **Conserver les informations de récupération automatique pendant les \<n> jours** Utilisez cette option pour spécifier la durée pendant laquelle Visual Studio conserve les fichiers créés pour la récupération automatique.

## <a name="see-also"></a>Voir aussi
 [Options, boîte de dialogue](../../ide/reference/options-dialog-box-visual-studio.md)
