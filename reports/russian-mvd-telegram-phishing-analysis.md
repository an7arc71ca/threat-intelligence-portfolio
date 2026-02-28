markdown
# Threat Analysis: Russian MVD Warns of Telegram-Based Gosuslugi Code Theft (February 2026)

**Author:** Artem Chuprov  
**Date:** March 2026  
**Language of Original Source:** Russian  
**Original Source:** Ministry of Internal Affairs of the Russian Federation  
**Original Article:** [МВД РФ назвали схему мошенников для выманивания кода от "Госуслуг" через Telegram](https://iz.ru/2049076/2026-02-26/mvd-rf-nazvali-shemu-moshennikov-dlia-vymanyvaniia-koda-ot-gosuslug-cherez-telegram)  
**English Summary:** [Ministry of Internal Affairs of the Russian Federation called a scheme of scammers to lure the code from "Public Services" through Telegram](https://en.iz.ru/en/2049076/2026-02-26/ministry-internal-affairs-russian-federation-called-scheme-schemers-lure-code-public-services)

---

## 1. Executive Summary

On February 26, 2026, the Russian Ministry of Internal Affairs (MVD) issued an urgent warning about a new phishing campaign targeting users of the Gosuslugi (State Services) portal. Scammers pose as delivery service employees on Telegram to trick victims into revealing SMS authentication codes, thereby gaining unauthorized access to their government service accounts. This report translates and analyzes the original Russian-language alert, maps the tactics to the MITRE ATT&CK framework, and provides actionable recommendations.

This alert is significant because Gosuslugi is Russia's primary e-government portal, containing passport data, tax information, property records, and links to banking services. Compromised accounts can lead to identity theft, financial fraud, and further targeted attacks.

---

## 2. Original Alert Translation

**Source:** МВД России назвали схему мошенников для выманивания кода от "Госуслуг" через Telegram  
**Date:** February 26, 2026  
**Original URL:** [https://iz.ru/2049076/2026-02-26/mvd-rf-nazvali-shemu-moshennikov-dlia-vymanyvaniia-koda-ot-gosuslug-cherez-telegram](https://iz.ru/2049076/2026-02-26/mvd-rf-nazvali-shemu-moshennikov-dlia-vymanyvaniia-koda-ot-gosuslug-cherez-telegram)

> *"The scammers pose as employees of the delivery service and use the Telegram messenger to lure the code from the Gosuslugi portal. This was announced on February 26 by the Russian Interior Ministry.*
>
> *As TASS clarified, one of the ways is to call a person on behalf of a delivery service employee. The attacker asks the victim to dictate the code from a so-called official verification bot, which is actually the access code to the account on Gosuslugi.*
>
> *The agency advised Russians not to transfer any codes to unknown persons, and to check delivery status using only official websites."*

---

## 3. Threat Landscape Context

This alert is part of a broader surge in Russian cybercrime. According to the Russian Interior Ministry's cybercrime division, in just one month (February 2026), Telegram-based scams contributed to more than **13,000 crimes with damages exceeding 15 billion rubles ($195.5 million)** .

The MVD has noted that scammers frequently use plausible everyday scenarios to gain trust. Common lures include:
- Fake delivery service calls (the current campaign)
- Pretending to be utility workers needing to "verify" water meters
- Posing as medical clinics requesting appointment confirmation
- Impersonating the Russian Postal Service about "package delivery"

These scams share a common goal: tricking victims into revealing the SMS code that grants access to their Gosuslugi account.

---

## 4. Technical Analysis

### 4.1 Attack Flow
INITIAL CONTACT
└── Victim receives Telegram message or call from "delivery service"
└── Scammer claims a package is waiting for delivery
└── Victim is told they must "verify identity" to receive package

SOCIAL ENGINEERING
└── Scammer sends a "verification bot" link or asks to call via Telegram
└── Victim receives legitimate SMS code from Gosuslugi (unaware)
└── Scammer asks victim to "confirm by reading the code"

ACCOUNT TAKEOVER
└── Scammer enters code on Gosuslugi login page
└── Attacker gains full access to victim's account
└── Account used for identity theft, fraud, or further attacks

text

### 4.2 MITRE ATT&CK Mapping

| Technique | ID | Description |
|-----------|----|-------------|
| Phishing: Spearphishing via Service | T1566.003 | Attackers use Telegram (legitimate service) to deliver phishing messages |
| Phishing: Voice Phishing (Vishing) | T1598.003 | Scammers make direct calls impersonating delivery services |
| Multi-Factor Authentication Interception | T1111 | SMS codes for MFA are stolen through social engineering |
| Account Manipulation | T1098 | Attacker gains control of victim's Gosuslugi account |
| Credential Dumping | T1003 | Access to account exposes personal data, tax records, banking links |

### 4.3 Key Observations

- **No Malware Required:** This attack relies entirely on social engineering, making it harder to detect with traditional security tools
- **Telegram as Attack Vector:** Scammers exploit Telegram's popularity and bot functionality to appear legitimate
- **SMS MFA Vulnerability:** The attack highlights a weakness in SMS-based authentication—the code can be stolen through user manipulation
- **Scale:** The MVD reports that despite some bot removals, new fraudulent bots appear constantly

---

## 5. Geopolitical and Regional Context

### 5.1 Gosuslugi as a High-Value Target

Gosuslugi (Единый портал государственных услуг) is Russia's centralized government services portal with over 100 million registered users. It contains:
- Passport and personal identification data
- Tax records and declarations
- Property ownership information
- Vehicle registration details
- Education certificates
- Links to banking services

Compromising a Gosuslugi account provides attackers with a complete "digital profile" of the victim.

### 5.2 Cross-Border Crime Elements

The Russian Interior Ministry estimates that **70-80% of cybercrimes targeting Russians are committed by individuals outside the country**, primarily from Ukraine, Baltic states, and former Soviet republics. This adds geopolitical complexity to threat attribution and law enforcement.

### 5.3 Government Response

In response to rising threats, Russia has implemented:
- Stricter SIM card registration requirements
- A new national biometric database (planned for April 2026)
- Enhanced bank monitoring and transaction limits
- Cross-border cooperation agreements with neighboring countries
- Gosuslugi's anti-fraud service with over 3 million users

---

## 6. Indicators of Compromise (IOCs)

Based on the MVD alert and associated reports, potential IOCs include:

| Type | Indicator | Notes |
|------|-----------|-------|
| Telegram Bot | Various "@delivery_bot" style usernames | Attackers create bots impersonating delivery services |
| Phone Numbers | Spoofed Russian mobile numbers | Often using VoIP to appear local |
| Domain Names | Fake delivery service websites | Used as secondary phishing lures |
| Message Patterns | "Confirm your delivery by sending the code from SMS" | Common phrasing in these attacks |

---

## 7. Recommendations

### For Russian Citizens and Russian-Speaking Users:

1. **Never share SMS codes:** No legitimate delivery service, government agency, or bank will ask for an SMS code over phone or messaging apps

2. **Verify independently:** If contacted about a delivery, check directly on the official website or app of the delivery service—never through links provided in messages

3. **Enable additional security:** Gosuslugi offers anti-fraud services and account activity monitoring

4. **Recognize pressure tactics:** Scammers create urgency ("your package will be returned," "immediate action required") to bypass rational thinking

5. **Report suspicious contacts:** Use Gosuslugi's built-in reporting features and notify local police

### For Organizations (International):

1. **Educate Russian-speaking employees** about this specific scam pattern, as they may be targeted through personal accounts

2. **Monitor for credential stuffing** attempts that may follow large-scale Gosuslugi compromises

3. **Consider alternate MFA methods** for high-value accounts, as SMS-based authentication is vulnerable to social engineering

4. **Incorporate Russian-language threat intelligence** into security monitoring, as scams often cross borders

### For Threat Intelligence Professionals:

This campaign demonstrates the importance of:
- **Multilingual monitoring:** English-only threat feeds miss critical regional alerts
- **Social engineering awareness:** Technical controls alone cannot prevent user manipulation
- **Cross-platform threats:** Attacks increasingly blend messaging apps (Telegram), phone calls, and web services

---

## 8. Conclusion

The February 2026 Russian MVD alert about Telegram-based Gosuslugi code theft illustrates a sophisticated, purely social-engineering attack targeting a critical government service. With losses exceeding 15 billion rubles monthly from Telegram-related scams, this represents a significant and ongoing threat.

My fluency in Russian allows me to access primary sources like this MVD alert, translate them accurately, and extract actionable intelligence that English-only analysts would miss. By monitoring Russian-language cybersecurity sources, I can provide early warning of emerging threats and help organizations protect Russian-speaking users and assets.

---

## 9. References

1. Izvestia. (2026, February 26). "МВД РФ назвали схему мошенников для выманивания кода от 'Госуслуг' через Telegram." [Original Russian]
2. Izvestia English. (2026, February 26). "Ministry of Internal Affairs of the Russian Federation called a scheme of scammers to lure the code from 'Public Services' through Telegram." [English summary]
3. Anadolu Ajansı. (2026, February 21). "Russia claims Telegram used to collect data on military, police, government officials for sabotage, terrorism."
4. Xinhua / Sohu. (2026, January 12). "《半月谈》：俄罗斯如何应对电诈"黑手"?" [Background on Russian anti-fraud efforts]
5. ФедералПресс. (2026, January 2). "Эти фразы используют мошенники: в МВД назвали типовые сценарии обмана по телефону."
6. MITRE ATT&CK Framework. (n.d.). Retrieved March 2026, from https://attack.mitre.org/

---

*This analysis is part of my threat intelligence portfolio. I am actively seeking remote Threat Intelligence roles where I can leverage my Russian fluency, engineering background, and cybersecurity expertise.*
