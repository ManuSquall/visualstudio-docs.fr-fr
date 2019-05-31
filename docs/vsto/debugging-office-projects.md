---
title: Déboguez des projets Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8b48335ccaa8bd21cf9f6e108d043ecf706903bb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441881"
---
# <a name="debug-office-projects"></a>Déboguez des projets Office
  Vous pouvez déboguer des projets Office à l'aide des mêmes outils Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que ceux que vous utilisez pour d'autres projets [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Les fonctionnalités du débogueur[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] telles que la capacité d'insérer des points d'arrêt et d'afficher des variables dans la fenêtre **Variables locales** , sont également disponibles lorsque vous déboguez des projets Office. Pour plus d’informations sur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] outils de débogage, consultez [déboguer dans Visual Studio](../debugger/debugging-in-visual-studio.md).

> [!TIP]
> Pour simplifier le débogage, fermez toutes les instances ouvertes de l'application Office avant de la générer et de la déboguer.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

> [!NOTE]
> Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle de compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office peu encombrantes par rapport aux compléments VSTO et de solutions, et vous pouvez les créer à l’aide de presque toutes les technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation web.

## <a name="start-and-stop-the-debugger"></a>Démarrer et arrêter le débogueur
 Vous pouvez démarrer le débogage d’un projet Office comme vous commencez à déboguer d’autres [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projets ; par exemple, vous pouvez appuyer sur la **F5** clé. Lorsque vous démarrez le débogage d’un projet de complément VSTO, un nouveau processus pour l’application Office cible est démarré et le composant logiciel complément VSTO est chargé.

 Lorsque vous commencez à déboguer un projet de niveau document, le document ou le classeur s'ouvre dans un nouveau processus Word ou Excel.

 Lorsque vous arrêtez le débogueur, ce dernier met brusquement fin au processus d'application, ou se détache si vous l'avez configuré pour cela. Tous les autres documents ouverts dans le processus d'application Office arrêté sont également fermés sans avertissement, et les modifications non enregistrées sont perdues. Cela inclut tous les documents ou classeurs qui sont ouverts pendant que le débogueur est en cours d'exécution.

 En général, il est préférable de se détacher du processus avant d'arrêter le débogueur, afin de pouvoir quitter l'application Office de manière normale. Vous pouvez également vous détacher d'abord du processus si vous souhaitez toujours utiliser un document ou une feuille de calcul après l'arrêt du débogueur.

 Si vous déboguez une personnalisation au niveau du document pour Word, l'arrêt répété du débogueur et la fermeture soudaine de Word peuvent endommager le modèle Normal. Si cela se produit, vous pouvez supprimer le modèle Normal endommagé : il sera automatiquement recréé à la prochaine ouverture de Word. Toutefois, les macros qui étaient stockées dans le modèle Normal ne sont pas recréées.

### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Déboguer des compléments Office 2013 VSTO à l’aide d’Office 2013 ou d’Office 2016
 Si vous utilisez Visual Studio 2015, et que les deux versions d’Office sont installées côte à côte, Visual Studio démarre Office 2016. Si vous utilisez Visual Studio 2013, Visual Studio démarre Office 2013.

 Si vous voulez déboguer votre complément VSTO à l’aide d’une autre version d’Office (2013 ou 2016), ouvrez le **Concepteur de projets**, et sous l’onglet **Déboguer** , choisissez la case d’option **Démarrer le programme externe** . Accédez ensuite à l'emplacement de l'exécutable d'application Office approprié.

## <a name="f10-and-f11-behavior"></a>Comportement des touches F10 et F11
 Lorsque vous démarrez le débogage d’un projet Office, **F10** et **F11** n’ont pas le même comportement que lorsque vous démarrez le débogage des autres projets Visual Basic ou c#. Dans les projets Visual Basic ou C#, le débogueur s'arrête sur la fonction principale (main) ; dans des projets Office, Visual Studio n'a pas le contrôle sur la fonction principale de l'application Office. Toutefois, pendant le débogage, **F10** et **F11** n’ont pas les mêmes fonctions que dans les projets Visual Basic et c#.

## <a name="display-exceptions"></a>Afficher les exceptions
 En raison de la façon dont le code managé interagit avec le code non managé, Visual Studio n'affiche pas les erreurs générées par les applications Microsoft Office. Par exemple, si un complément VSTO créé à l’aide des outils de développement Office dans Visual Studio lève une exception, l’application Microsoft Office poursuit sans afficher d’erreur. Pour consulter ces erreurs, configurez le débogueur pour qu'il s'arrête sur les exceptions Common Language Runtime. Pour plus d’informations, consultez [gérer les exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md).

 Si vous configurez le débogueur pour qu'il s'arrête sur les exceptions Common Langage Runtime, toutes les exceptions s'arrêteront alors dans le débogueur, y compris celles que vous avez gérées et certaines exceptions de première chance du runtime lui-même, qui peuvent ne pas concerner votre projet. Des erreurs faisant référence au fait que msosec est introuvable apparaissent dans chaque projet, mais peuvent être ignorées en toute sécurité. Ces exceptions msosec n'affecteront pas votre solution.

 Vous pouvez également utiliser des instructions **Try...Catch** autour de vos méthodes pour intercepter les exceptions.

 Par défaut, Visual Studio n'affiche pas non plus les erreurs de débogage juste-à-temps pour les projets Office ; toutefois, vous pouvez activer cette fonctionnalité pour consulter les erreurs générées. Pour plus d’informations, consultez [juste-à-temps de débogage dans Visual Studio](../debugger/just-in-time-debugging-in-visual-studio.md).

## <a name="command-line-arguments"></a>Arguments de ligne de commande
 Si le **Action de démarrage** sur le **déboguer** page de propriété est définie sur **démarrer le projet**, Visual Studio n’utilise pas les arguments de ligne de commande lors du débogage du projet, même si vous avez spécifié des arguments de ligne de commande comme options de démarrage. Si vous souhaitez utiliser des arguments de ligne de commande lorsque vous démarrez le débogage, vous devez sélectionner un **Action de démarrage** autre que **démarrer le projet**.

## <a name="source-control"></a>Contrôle de code source
 Les propriétés de débogage ne sont pas partagées entre plusieurs utilisateurs sous contrôle de code source. Les projets Visual Basic et C# stockent les propriétés de débogage dans un fichier spécifique à l'utilisateur (*Nom_projet*.vbproj.user ou *Nom_projet*.csproj.user), et ce fichier n'est pas sous contrôle de code source. Si plusieurs personnes effectuent un débogage, chacune d'entre elles doit entrer manuellement les propriétés de débogage.

## <a name="debug-cached-datasets-in-a-document-level-project"></a>Déboguer des jeux de données mis en cache dans un projet au niveau du document
 Chaque fois que vous générez un projet, le groupe de données est vidé et recréé. Si vous souhaitez déboguer un groupe de données mis en cache, vous devez ouvrir le document en dehors de Visual Studio, puis attacher le débogueur.

## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Projets de document Word de débogage basés sur le Document Word 97-2003 (* .doc) format
 Pour déboguer un projet de Document Word basé sur un Document Word 97-2003 ( */* .doc *) format, vous devez ajouter le dossier du projet à la liste de dossiers approuvés. Pour plus d’informations sur la façon de procéder, consultez [accorder une confiance aux documents](../vsto/granting-trust-to-documents.md).

## <a name="debug-disabled-add-ins"></a>Débogage désactivé des compléments
 Les applications Microsoft Office peuvent désactiver les compléments VSTO qui se comportent de façon inattendue. Une application Microsoft Office désactive les compléments VSTO pour empêcher le chargement de tout code problématique chaque fois qu’elle démarre. Toutefois, il est également facile de provoquer un comportement inattendu au cours d'un débogage classique. Pour plus d’informations sur la façon de réactiver les Compléments VSTO, consultez [Comment : Réactiver un complément qui a été désactivé](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).

 Les applications Microsoft Office utilisent deux types de désactivation pour les compléments VSTO : dure et douce.

### <a name="hard-disabling"></a>La désactivation dure
 La désactivation dure peut se produire quand un complément, VSTO entraîne la fermeture inattendue de l’application. Elle peut également se produire sur votre ordinateur de développement si vous arrêtez le débogueur pendant que le gestionnaire d'événements <xref:Microsoft.Office.Tools.AddIn.Startup> de votre complément VSTO est en cours d'exécution. Une fois un VSTO Add-in désactivation dure, il apparaît dans le **éléments désactivés** liste dans l’application.

 Si une application Office dure désactive un complément VSTO créé à l’aide des outils de développement Office dans Visual Studio, l’application désactive uniquement le complément VSTO qui a provoqué l’échec. Les autres compléments VSTO créés à l’aide des outils de développement Office dans Visual Studio pour cette application Office continuent à se charger.

### <a name="soft-disabling"></a>La désactivation douce
 La désactivation en douceur peut se produire quand un complément VSTO génère une erreur qui n'entraîne pas la fermeture inattendue de l'application. Par exemple, une application peut entraîner la désactivation en douceur d'un complément VSTO, si ce dernier lève une exception non gérée pendant l'exécution du gestionnaire d'événements <xref:Microsoft.Office.Tools.AddIn.Startup> . Une fois un VSTO Add-in d’une désactivation douce, il apparaît dans le **des compléments d’applications inactifs** liste dans l’application et l’application modifie la valeur de la **LoadBehavior** entrée de Registre pour le composant logiciel complément VSTO pour indiquer qu’il est déchargé. Pour plus d’informations sur la **LoadBehavior** l’entrée de Registre, consultez [les entrées de Registre pour les Compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Résoudre les erreurs d’installation à l’aide de l’Observateur d’événements
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] écrit des messages dans l'observateur d'événements de Windows, pour toutes les exceptions levées lors de l'installation ou de la désinstallation des solutions Office. Vous pouvez utiliser ces messages pour résoudre les éventuels problèmes d'installation et de déploiement.

## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Résoudre les erreurs de démarrage à l’aide d’un journal des fichiers et messages d’erreur
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] peut consigner toutes les erreurs qui se produisent au démarrage dans un fichier journal ou afficher chacune d'elles dans une boîte de message. Par défaut, ces options sont désactivées. Vous pouvez activer les options en créant des variables d’environnement.

 Pour afficher chaque erreur dans une boîte de message, créez une variable d'environnement nommée `VSTO_SUPPRESSDISPLAYALERTS` et affectez-lui la valeur 0 (zéro). Vous pouvez supprimer les messages en supprimant la variable d'environnement ou en lui affectant la valeur 1 (un).

 Pour consigner les erreurs dans un fichier journal, créez une variable d'environnement appelée `VSTO_LOGALERTS` et affectez-lui la valeur 1 (un). [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crée le fichier journal dans le dossier qui contient le manifeste de déploiement du complément VSTO, ou dans le dossier qui contient le document ou le classeur associé à la personnalisation. Si cette tentative échoue, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crée le fichier journal local *%temp%* dossier. Pour les compléments VSTO de niveau application, le nom par défaut est *Nom_complément*.vsto.log. Pour les projets de niveau document, le nom du fichier journal est *Nom_document*.*extension*.log ; par exemple, ExcelWorkbook1.xlsx.log. Pour arrêter la journalisation des erreurs, supprimez la variable d'environnement ou affectez-lui la valeur 0 (zéro).

## <a name="see-also"></a>Voir aussi

- [Générer des solutions Office](../vsto/building-office-solutions.md)
- [Guide pratique pour Réactiver un complément qui a été désactivé](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)
- [Programmer des Compléments VSTO](../vsto/programming-vsto-add-ins.md)