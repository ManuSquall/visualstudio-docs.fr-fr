---
title: "CA1704 : Les identificateurs doivent &#234;tre correctement orthographi&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 25
---
# CA1704 : Les identificateurs doivent &#234;tre correctement orthographi&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldBeSpelledCorrectly|  
|CheckId|CA1704|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Oui|  
  
## Cause  
 Le nom d'un identificateur contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du correcteur orthographique Microsoft.  Cette règle ne vérifie pas les constructeurs ou les membres avec une dénomination spéciale tels les accesseurs de propriété get et set.  
  
## Description de la règle  
 Cette règle analyse l'identificateur dans des jetons et vérifie l'orthographe de chaque jeton.  L'algorithme d'analyse effectue les transformations suivantes :  
  
-   Les lettres majuscules démarrent un nouveau jeton.  À titre d'exemple, MonNomestJosé régit sous forme de jeton "Mon", "Nom", "Est" et "José".  
  
-   Dans le cas de plusieurs lettres majuscules, la dernière lettre majuscule commence par un nouveau jeton.  À titre d'exemple, ÉditeurGUI régit sous forme de jeton "Éditeur" et "GUI".  
  
-   Les apostrophes à gauche ou à droite sont supprimées.  À titre d'exemple, 'expéditeur' régit sous forme de jeton "expéditeur".  
  
-   Les traits de soulignement signifient la fin d'un jeton et sont supprimés.  À titre d'exemple, Bonjour\_monde régit sous forme de jeton "Bonjour" et "monde".  
  
-   Les perluètes incorporées sont supprimées.  À titre d'exemple, for&mat régit sous forme de jeton "format".  
  
 La version anglaise \(en\) du vérificateur d'orthographe est utilisée par défaut.  Aucun autre dictionnaire de langue n'est actuellement disponible.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, corrigez l'orthographe du mot ou ajoutez le mot à un dictionnaire personnalisé nommé CustomDictionary.xml.  Placez ce dictionnaire dans le répertoire d'installation de l'outil, le répertoire du projet ou le répertoire associé à l'outil sous le profil de l'utilisateur \(%USERPROFILE%\\Application Data\\...\).  Pour apprendre à ajouter le dictionnaire personnalisé à un projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consultez [Comment : personnaliser le dictionnaire d’analyse du code](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)  
  
-   Ajoutez les mots qui ne doivent pas provoquer de violation sous Dictionary\/Words\/Recognized path.  
  
-   Ajoutez les mots qui doivent provoquer une violation sous Dictionary\/Words\/Unrecognized path.  
  
-   Ajoutez les mots qui doivent être signalés comme obsolètes sous Dictionary\/Words\/Deprecated path.  Consultez la rubrique associée [CA1726 : Utilisez les termes par défaut](../code-quality/ca1726-use-preferred-terms.md) pour plus d'informations.  
  
-   Ajoutez les exceptions aux règles de casse des acronymes de Dictionary\/Acronyms\/CasingExceptions path.  
  
 Les éléments suivants sont un exemple de la structure d'un fichier de dictionnaire personnel.  
  
```  
<Dictionary>  
   <Words>  
      <Unrecognized>  
         <Word>cb</Word>  
      </Unrecognized>  
      <Recognized>  
         <Word>stylesheet</Word>  
         <Word>GotDotNet</Word>  
      </Recognized>  
      <Deprecated>  
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>  
      </Deprecated>  
   </Words>  
   <Acronyms>  
      <CasingExceptions>  
         <Acronym>CJK</Acronym>  
         <Acronym>Pi</Acronym>  
      </CasingExceptions>  
   </Acronyms>  
</Dictionary>  
```  
  
## Quand supprimer les avertissements  
 Supprimez uniquement un avertissement de cette règle si le mot est intentionnellement mal orthographié et que le mot s'applique à un jeu limité de la bibliothèque.  Les mots épelés correctement réduisent la durée d'apprentissage requise pour les nouvelles bibliothèques de logiciels.  
  
## Règles connexes  
 [CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703 : L'orthographe des chaînes de ressources doit être correcte](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726 : Utilisez les termes par défaut](../code-quality/ca1726-use-preferred-terms.md)  
  
## Voir aussi  
 [Comment : personnaliser le dictionnaire d’analyse du code](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)