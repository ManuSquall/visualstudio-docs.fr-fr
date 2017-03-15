---
title: "Cr&#233;er un projet de test unitaire | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a608bfba-1a43-4a60-b73a-1fe53ef58098
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "mlearned"
manager: "douge"
---
# Cr&#233;er un projet de test unitaire
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Tests unitaires reflètent souvent la structure du code sous test. Par exemple, un projet de test unitaire serait être créé pour chaque projet de code dans le produit. Le projet de test peut être dans la même solution que le code de production, ou il peut être dans une solution distincte. Vous pouvez avoir plusieurs unités de tester les projets dans une solution.  
  
> [!NOTE]
>  L’emplacement de l’unité de code natif et la structure de projet de test peut être différente de celle qui est décrite dans cette rubrique. Pour plus d’informations, consultez [Ajouter des tests unitaires pour les applications C++ existantes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md).  
  
## <a name="to-create-a-unit-test-project"></a>Pour créer un projet de test unitaire :  
  
1.  Dans le menu **Fichier** , choisissez **Nouveau** , puis **Projet** (Ctrl+Maj+N).  
  
2.  Dans la boîte de dialogue Nouveau projet, développez le **installé** nœud, choisissez la langue que vous souhaitez utiliser pour votre projet de test, puis choisissez **Test**.  
  
3.  Pour utiliser l’une des infrastructures de tests unitaires Microsoft, choisissez **Projet de test unitaire** dans la liste des modèles de projet. Sinon, choisissez le modèle de projet de l’infrastructure de tests unitaires que vous souhaitez utiliser. Pour tester le projet de comptes de notre exemple, vous devez nommer le projet AccountsTests.  
  
4.  Dans votre projet de test unitaire, ajoutez une référence à du code sous test.  Voici comment créer la référence à un projet de code dans la même solution :  
  
    1.  Sélectionnez le projet dans l’Explorateur de solutions.  
  
    2.  Sur le **projet** menu, choisissez **Ajouter une référence...**.  
  
    3.  Dans la boîte de dialogue Gestionnaire de références, ouvrez le **Solution** nœud et choisissez **projets**. Vérifiez le nom de projet de code et fermez la boîte de dialogue.  
  
5.  Si le code que vous souhaitez tester est dans un autre emplacement, consultez la page [Gestion des références dans un projet](../ide/managing-references-in-a-project.md) Pour plus d’informations sur l’ajout de références.  
  
## <a name="next-steps"></a>Étapes suivantes  
 **Pour écrire des tests unitaires**  
  
 Consultez les sections suivantes :  
  
-   [Écrivez des Tests unitaires pour le .NET Framework avec l’infrastructure de Test unitaire Microsoft pour le Code managé](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)  
  
-   [Écrivez des tests unitaires pour C/C++ avec l’infrastructure de test unitaire Microsoft pour C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)  
  
 **Exécution de tests unitaires**  
  
 [Exécuter des tests unitaires avec Test Explorer](../test/run-unit-tests-with-test-explorer.md)