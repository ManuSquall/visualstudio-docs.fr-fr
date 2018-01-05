---
title: "Analyse du code pour une vue d’ensemble du Code managé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: b705abb680276faf9d4311cd21cae1b103c4a09d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="code-analysis-for-managed-code-overview"></a>Analyse du code pour une vue d’ensemble du code managé

L'outil d'analyse du code managé analyse les assemblys et signale les informations à leur sujet, notamment les violations des règles de programmation et de design présentées dans les règles de conception de Microsoft .NET Framework.

L'outil d'analyse représente les contrôles effectués lors d'une analyse comme messages d'avertissement. Les messages d'avertissement identifient les problèmes de programmation et de conception pertinents et, si possible, fournissent des informations relatives à leur résolution.

## <a name="ide-integrated-development-environment-integration"></a>Intégration IDE (environnement de développement intégré)

Vous pouvez exécuter l’analyse du code sur votre projet manuellement ou automatiquement.

Pour exécuter l’analyse du code chaque fois que vous générez un projet, sélectionnez **activer l’analyse du Code sur la Build** sur la Page de propriétés du projet. Pour plus d’informations, consultez [Comment : activer et désactiver l’analyse du Code automatique](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Pour exécuter manuellement l’analyse du code sur un projet, dans la barre de menus, choisissez **analyser** > **exécuter l’analyse du Code** > **exécuter l’analyse du Code sur <project>** . Pour plus d’informations, consultez [Comment : activer et désactiver l’analyse du Code automatique](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="rule-sets"></a>Ensembles de règles

Règles d’analyse du code pour le code managé sont regroupés en *ensembles de règles*. Vous pouvez utiliser l'un des ensembles de règles standard Microsoft ou créer un ensemble de règles personnalisé pour répondre à un besoin particulier. Pour plus d’informations, consultez [à l’aide des ensembles de règles à un groupe de règles d’analyse du Code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

## <a name="in-source-suppression"></a>Dans la suppression de la source

Bien souvent, il est utile d'indiquer qu'un avertissement ne s'applique pas. Cela permet d’informer le développeur et les éventuels réviseurs de code, qu’un avertissement a fait l’objet d’une analyse, puis a été supprimé ou ignoré.

Dans la source de la suppression des avertissements est implémentée via des attributs personnalisés. Pour supprimer un avertissement, ajoutez l'attribut `SuppressMessage` au code source comme indiqué dans l'exemple suivant :

```csharp
[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Pour plus d’informations, consultez [supprimer les avertissements par à l’aide de l’attribut SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Exécuter l’analyse du code dans le cadre de la stratégie d’archivage

En tant qu'organisation, vous pourriez demander à ce que tous les archivages respectent certaines stratégies. En particulier, vous souhaitez vous assurer que vous suivez ces règles :

- Il n’y a aucune erreur de build dans le code en cours d’archivage.

- Analyse du code est exécutée dans le cadre de la build la plus récente.

Vous pouvez l’effectuer en spécifiant des stratégies d’archivage. Pour plus d’informations, consultez [améliorer la qualité du Code avec les stratégies d’archivage projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Intégration de Team build

Vous pouvez utiliser les fonctionnalités intégrées du système de génération pour exécuter l’outil d’analyse dans le cadre du processus de génération. Pour plus d’informations, consultez [créer et libérer (VSTS)](/vsts/build-release/index).

## <a name="see-also"></a>Voir aussi

[À l’aide de la règle définit aux règles d’analyse de Code de groupe](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
[Comment : activer et désactiver l’analyse du Code automatique](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)