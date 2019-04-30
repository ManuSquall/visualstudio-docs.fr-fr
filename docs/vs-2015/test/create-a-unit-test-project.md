---
title: Créer un projet de test unitaire | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a608bfba-1a43-4a60-b73a-1fe53ef58098
caps.latest.revision: 10
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f792c29b50be5bbadf34980b81f7c5dd329cccfb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442831"
---
# <a name="create-a-unit-test-project"></a>Créer un projet de test unitaire
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les tests unitaires reflètent souvent la structure du code testé. Par exemple, un projet de test unitaire est créé pour chaque projet de code du produit. Le projet de test peut se trouver dans la même solution que le code de production, ou dans une solution distincte. Vous pouvez avoir plusieurs projets de test unitaire dans une solution.  
  
> [!NOTE]
> L’emplacement des tests unitaires du code natif et la structure du projet de test peuvent être différents de la structure décrite dans cette rubrique. Pour plus d’informations, consultez [Ajout de tests unitaires aux applications C++ existantes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md).  
  
## <a name="to-create-a-unit-test-project"></a>Pour créer un projet de test unitaire :  
  
1. Dans le menu **Fichier** , choisissez **Nouveau** , puis **Projet** (Ctrl+Maj+N).  
  
2. Dans la boîte de dialogue Nouveau projet, développez le nœud **Installé**, choisissez le langage à utiliser pour votre projet de test, puis sélectionnez **Test**.  
  
3. Pour utiliser l’une des infrastructures de tests unitaires Microsoft, choisissez **Projet de test unitaire** dans la liste des modèles de projet. Sinon, choisissez le modèle de projet du framework de tests unitaires que vous souhaitez utiliser. Pour tester le projet Accounts de notre exemple, nommez le projet AccountsTests.  
  
4. Dans votre projet de test unitaire, ajoutez une référence au code testé.  Voici comment créer la référence à un projet de code dans la même solution :  
  
    1. Sélectionnez le projet dans l’Explorateur de solutions.  
  
    2. Dans le menu **Projet**, choisissez **Ajouter une référence**.  
  
    3. Dans la boîte de dialogue Gestionnaire de références, ouvrez le nœud **Solution** et choisissez **Projets**. Vérifiez le nom du projet de code et fermez la boîte de dialogue.  
  
5. Si le code que vous souhaitez tester se trouve à un autre emplacement, consultez [Gestion des références dans un projet](../ide/managing-references-in-a-project.md) pour plus d’informations sur l’ajout de références.  
  
## <a name="next-steps"></a>Étapes suivantes  
 **Écriture de tests unitaires**  
  
 Consultez l’une des sections suivantes :  
  
- [Écriture de tests unitaires pour le .NET Framework à l’aide de l’infrastructure de tests unitaires Microsoft pour le code managé](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)  
  
- [Écriture de tests unitaires pour C/C++ à l’aide du framework de tests unitaires Microsoft pour C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)  
  
  **Exécution de tests unitaires**  
  
  [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)
