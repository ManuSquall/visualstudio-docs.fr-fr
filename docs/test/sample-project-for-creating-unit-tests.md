---
title: "Exemple de projet pour la cr&#233;ation de tests unitaires | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "test unitaire (exemples Visual Studio)"
  - "tests unitaires, exemples"
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "mlearned"
manager: "douge"
---
# Exemple de projet pour la cr&#233;ation de tests unitaires
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cet exemple de code est fourni pour une utilisation dans les procédures suivantes :  
  
-   [Procédure pas à pas : création et exécution de tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  Cette procédure pas à pas vous guide à travers les étapes de création et de personnalisation des tests unitaires, de leur exécution et de l'examen des résultats des tests.  
  
-   [Walkthrough: Run tests and view code coverage](http://msdn.microsoft.com/fr-fr/d4aab8e2-2140-4975-b4e3-41ef3fa944c8).  Cette procédure pas à pas illustre comment afficher les données de couverture du code, qui affiche la proportion du code de votre projet en cours de test.  
  
-   [Procédure pas à pas : utilisation de l'utilitaire de test de ligne de commande](../Topic/Walkthrough:%20using%20the%20command-line%20test%20utility.md).  Dans cette procédure pas à pas, vous utilisez l'utilitaire de ligne de commande MSTest.exe pour exécuter les tests et afficher les résultats.  
  
## Exemple de code  
 L'unique erreur intentionnelle de cet exemple est que dans la méthode Debit « m\_balance \+\= amount » doit avoir le signe moins \(\-\) et non le signe plus \(\+\) devant le signe égal.  
  
```  
using System;   
  
namespace BankAccountNS  
{  
    /// <summary>   
    /// Bank Account demo class.   
    /// </summary>   
    public class BankAccount  
    {  
        private string m_customerName;  
  
        private double m_balance;  
  
        private bool m_frozen = false;  
  
        private BankAccount()  
        {  
        }  
  
        public BankAccount(string customerName, double balance)  
        {  
            m_customerName = customerName;  
            m_balance = balance;  
        }  
  
        public string CustomerName  
        {  
            get { return m_customerName; }  
        }  
  
        public double Balance  
        {  
            get { return m_balance; }  
        }  
  
        public void Debit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount > m_balance)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount; // intentionally incorrect code  
        }  
  
        public void Credit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount;  
        }  
  
        private void FreezeAccount()  
        {  
            m_frozen = true;  
        }  
  
        private void UnfreezeAccount()  
        {  
            m_frozen = false;  
        }  
  
        public static void Main()  
        {  
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);   
  
            ba.Credit(5.77);  
            ba.Debit(11.22);  
            Console.WriteLine("Current balance is ${0}", ba.Balance);  
        }  
  
    }  
}  
```  
  
 \/\* Les noms de sociétés, d'organisations, de produits, de domaines, d'adresses de messagerie, de logos, de personnes, de lieux et d'événements mentionnés dans les exemples sont fictifs.  Toute ressemblance avec des noms ou des événements réels est purement fortuite et involontaire.  \*\/  
  
## Utilisation du code  
 Pour utiliser ce code, vous devez d'abord créer un projet pour lui dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Suivez les étapes de la section « Préparation de la procédure pas à pas » dans [Procédure pas à pas : création et exécution de tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  
  
## Voir aussi  
 [Procédure pas à pas : création et exécution de tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [Walkthrough: Run tests and view code coverage](http://msdn.microsoft.com/fr-fr/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [Procédure pas à pas : utilisation de l'utilitaire de test de ligne de commande](../Topic/Walkthrough:%20using%20the%20command-line%20test%20utility.md)