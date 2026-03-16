[![Multi-Agent Design](../../../translated_images/sv/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Klicka på bilden ovan för att se videon av denna lektion)_

# Multi-agent designmönster

Så snart du börjar arbeta med ett projekt som involverar flera agenter, behöver du överväga multi-agent designmönster. Det kanske dock inte är omedelbart tydligt när man ska byta till multi-agenter och vilka fördelarna är.

## Introduktion

I denna lektion strävar vi efter att besvara följande frågor:

- Vilka scenarier är lämpliga för multi-agenter?
- Vilka är fördelarna med att använda multi-agenter istället för en enda agent som utför flera uppgifter?
- Vilka är byggstenarna för att implementera multi-agent designmönstret?
- Hur får vi insyn i hur flera agenter interagerar med varandra?

## Lärandemål

Efter denna lektion bör du kunna:

- Identifiera scenarier där multi-agenter är tillämpliga
- Känna igen fördelarna med att använda multi-agenter jämfört med en enda agent.
- Förstå byggstenarna för att implementera multi-agent designmönstret.

Vad är den större bilden?

*Multi-agenter är ett designmönster som tillåter flera agenter att arbeta tillsammans för att uppnå ett gemensamt mål*.

Detta mönster används brett inom olika områden, inklusive robotik, autonoma system och distribuerad databehandling.

## Scenarier där multi-agenter är tillämpliga

Vilka scenarier är då ett bra användningsfall för att använda multi-agenter? Svaret är att det finns många scenarier där flera agenter är fördelaktigt, särskilt i följande fall:

- **Stora arbetsvolymer**: Stora arbetsbördor kan delas upp i mindre uppgifter och tilldelas olika agenter, vilket möjliggör parallell bearbetning och snabbare slutförande. Ett exempel är vid en stor databehandlingsuppgift.
- **Komplexa uppgifter**: Komplexa uppgifter, likt stora arbetsvolymer, kan delas upp i mindre deluppgifter och tilldelas olika agenter, där varje agent är specialiserad på en specifik del av uppgiften. Ett bra exempel är autonoma fordon där olika agenter hanterar navigation, hinderupptäckt och kommunikation med andra fordon.
- **Mångsidig expertis**: Olika agenter kan ha olika expertis, vilket gör att de kan hantera olika aspekter av en uppgift mer effektivt än en enda agent. Ett exempel är inom vården där agenter kan hantera diagnostik, behandlingsplaner och patientövervakning.

## Fördelar med att använda multi-agenter jämfört med en enda agent

Ett system med en enda agent kan fungera bra för enkla uppgifter, men för mer komplexa uppgifter kan användning av flera agenter ge flera fördelar:

- **Specialisering**: Varje agent kan vara specialiserad på en specifik uppgift. Avsaknad av specialisering i en enda agent innebär att du har en agent som kan göra allt men som kan bli förvirrad över vad den ska göra när den ställs inför en komplex uppgift. Den kan till exempel göra en uppgift som den inte är bäst lämpad för.
- **Skalbarhet**: Det är lättare att skala system genom att lägga till fler agenter än att överbelasta en enda agent.
- **Felförtålighet**: Om en agent misslyckas kan andra fortsätta fungera, vilket säkerställer systemets tillförlitlighet.

Låt oss ta ett exempel: Vi bokar en resa åt en användare. Ett enkelt agentsystem skulle behöva hantera alla aspekter av resebokningsprocessen, från att hitta flyg till att boka hotell och hyrbilar. För att klara detta med en enda agent måste agenten ha verktyg för att hantera alla dessa uppgifter. Det kan leda till ett komplext och monolitiskt system som är svårt att underhålla och skala. Ett multi-agent-system skulle däremot kunna ha olika agenter specialiserade på att hitta flyg, boka hotell och hyrbilar. Detta skulle göra systemet mer modulärt, enklare att underhålla och skalbart.

Jämför detta med en resebyrå som drivs som en källarverksamhet jämfört med en resebyrå som drivs som en franchise. Källarverksamheten skulle ha en enda agent som hanterar alla aspekter av bokningsprocessen, medan franchisen skulle ha olika agenter som hanterar olika delar av bokningsprocessen.

## Byggstenar för att implementera multi-agent designmönstret

Innan du kan implementera multi-agent designmönstret behöver du förstå byggstenarna som utgör mönstret.

Låt oss göra detta mer konkret genom att återigen titta på exemplet med att boka en resa för en användare. I detta fall skulle byggstenarna inkludera:

- **Agentkommunikation**: Agenter för att hitta flyg, boka hotell och hyrbilar behöver kommunicera och dela information om användarens preferenser och begränsningar. Du behöver bestämma protokollen och metoderna för denna kommunikation. Vad detta konkret betyder är att agenten för att hitta flyg behöver kommunicera med agenten för att boka hotell för att försäkra att hotellet är bokat för samma datum som flyget. Det betyder att agenterna behöver dela information om användarens resdatum, vilket innebär att du behöver bestämma *vilka agenter som delar information och hur de delar den*.
- **Koordineringsmekanismer**: Agenter behöver koordinera sina handlingar för att säkerställa att användarens preferenser och begränsningar uppfylls. En användarpreferens kan vara att hen vill ha ett hotell nära flygplatsen medan en begränsning kan vara att hyrbilar endast finns tillgängliga på flygplatsen. Detta betyder att agenten för att boka hotell behöver koordinera med agenten för att boka hyrbilar för att säkerställa att användarens preferenser och begränsningar uppfylls. Det betyder att du behöver bestämma *hur agenterna koordinerar sina handlingar*.
- **Agentarkitektur**: Agenter behöver ha en intern struktur för att fatta beslut och lära sig av sina interaktioner med användaren. Det betyder att agenten för att hitta flyg behöver ha en intern struktur för att fatta beslut om vilka flyg som ska rekommenderas till användaren. Det betyder att du behöver bestämma *hur agenter fattar beslut och lär sig av sina interaktioner med användaren*. Exempel på hur en agent lär sig och förbättras kan vara att agenten för att hitta flyg kan använda en maskininlärningsmodell för att rekommendera flyg till användaren baserat på tidigare preferenser.
- **Insyn i multi-agent interaktioner**: Du behöver ha insyn i hur flera agenter interagerar med varandra. Det innebär att du behöver ha verktyg och tekniker för att spåra agenters aktiviteter och interaktioner. Detta kan vara i form av loggning och övervakningsverktyg, visualiseringsverktyg och prestandamått.
- **Multi-agent mönster**: Det finns olika mönster för att implementera multi-agent system, såsom centraliserade, decentraliserade och hybrida arkitekturer. Du behöver välja mönster som passar bäst för ditt användningsfall.
- **Människa i loopen**: I de flesta fall har du en människa i loopen och du behöver instruera agenterna när de ska be om mänskligt ingripande. Detta kan ske i form av att en användare begär ett specifikt hotell eller flyg som agenterna inte har rekommenderat, eller begär bekräftelse innan bokning av flyg eller hotell.

## Insyn i multi-agent interaktioner

Det är viktigt att du har insyn i hur flera agenter interagerar med varandra. Denna insyn är avgörande för felsökning, optimering och att säkerställa systemets övergripande effektivitet. För att uppnå detta behöver du ha verktyg och tekniker för att spåra agenteras aktiviteter och interaktioner. Detta kan vara i form av loggnings- och övervakningsverktyg, visualiseringsverktyg och prestandamått.

Till exempel, vid bokning av en resa åt en användare, kan du ha en instrumentpanel som visar status för varje agent, användarens preferenser och begränsningar, samt interaktionerna mellan agenterna. Denna instrumentpanel kan visa användarens resdatum, de flyg som rekommenderas av flygagenten, hotellen som rekommenderas av hotellagenten och hyrbilarna som rekommenderas av hyrbilsagenten. Detta ger dig en tydlig bild av hur agenterna interagerar med varandra och om användarens preferenser och begränsningar uppfylls.

Låt oss titta närmare på varje aspekt.

- **Loggning och övervakningsverktyg**: Du vill ha loggning för varje åtgärd som en agent utför. En loggpost kan spara information om agenten som utförde åtgärden, vilken åtgärd som togs, tidpunkten då åtgärden utfördes samt resultatet av åtgärden. Denna information kan sedan användas för felsökning, optimering med mera.

- **Visualiseringsverktyg**: Visualiseringsverktyg kan hjälpa dig att se interaktionerna mellan agenter på ett mer intuitivt sätt. Till exempel kan du ha en graf som visar informationsflödet mellan agenter. Detta kan hjälpa dig identifiera flaskhalsar, ineffektiviteter och andra problem i systemet.

- **Prestandamått**: Prestandamått kan hjälpa dig att följa effektiviteten hos multi-agent systemet. Till exempel kan du mäta tiden som krävs för att slutföra en uppgift, antal uppgifter slutförda per tidsenhet och noggrannheten i rekommendationerna som görs av agenterna. Denna information kan hjälpa dig att identifiera förbättringsområden och optimera systemet.

## Multi-agent mönster

Låt oss dyka ned i några konkreta mönster vi kan använda för att skapa multi-agent-appar. Här är några intressanta mönster värda att överväga:

### Gruppchatt

Detta mönster är användbart när du vill skapa en gruppchatt-applikation där flera agenter kan kommunicera med varandra. Typiska användningsfall för detta mönster inkluderar teamarbete, kundsupport och sociala nätverk.

I detta mönster representerar varje agent en användare i gruppchatten, och meddelanden utbyts mellan agenter med hjälp av ett meddelandeprotokoll. Agenterna kan skicka meddelanden till gruppchatten, ta emot meddelanden från gruppchatten och svara på meddelanden från andra agenter.

Detta mönster kan implementeras med en centraliserad arkitektur där alla meddelanden dirigeras genom en central server eller en decentraliserad arkitektur där meddelanden utbyts direkt.

![Group chat](../../../translated_images/sv/multi-agent-group-chat.ec10f4cde556babd.webp)

### Överlämning

Detta mönster är användbart när du vill skapa en applikation där flera agenter kan överlämna uppgifter till varandra.

Typiska användningsfall för detta mönster inkluderar kundsupport, uppgiftshantering och automatisering av arbetsflöden.

I detta mönster representerar varje agent en uppgift eller ett steg i ett arbetsflöde, och agenter kan överlämna uppgifter till andra agenter baserat på fördefinierade regler.

![Hand off](../../../translated_images/sv/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Samarbetsfiltrering

Detta mönster är användbart när du vill skapa en applikation där flera agenter kan samarbeta för att göra rekommendationer till användare.

Anledningen till att man vill att flera agenter samarbetar är att varje agent kan ha olika expertis och kan bidra till rekommendationsprocessen på olika sätt.

Låt oss ta ett exempel där en användare vill ha en rekommendation på den bästa aktien att köpa på aktiemarknaden.

- **Branschexpert**: En agent kan vara expert inom en viss bransch.
- **Teknisk analys**: En annan agent kan vara expert på teknisk analys.
- **Fundamental analys**: Och en tredje agent kan vara expert på fundamental analys. Genom att samarbeta kan dessa agenter ge en mer heltäckande rekommendation till användaren.

![Recommendation](../../../translated_images/sv/multi-agent-filtering.d959cb129dc9f608.webp)

## Scenario: Återbetalningsprocess

Tänk dig ett scenario där en kund försöker få en återbetalning för en produkt. Det kan finnas ganska många agenter involverade i denna process, men låt oss dela upp det mellan agenter specifika för denna process och generella agenter som kan användas i andra processer.

**Agenter specifika för återbetalningsprocessen**:

Följande är några agenter som kan vara involverade i återbetalningsprocessen:

- **Kundagent**: Denna agent representerar kunden och ansvarar för att initiera återbetalningsprocessen.
- **Säljagent**: Denna agent representerar säljaren och ansvarar för att behandla återbetalningen.
- **Betalningsagent**: Denna agent representerar betalningsprocessen och ansvarar för att återbetala kundens betalning.
- **Lösningsagent**: Denna agent representerar lösningsprocessen och ansvarar för att lösa eventuella problem som uppstår under återbetalningsprocessen.
- **Efterlevnadsagent**: Denna agent representerar efterlevnadsprocessen och ansvarar för att säkerställa att återbetalningsprocessen följer regler och policyer.

**Generella agenter**:

Dessa agenter kan användas av andra delar av din verksamhet.

- **Fraktagent**: Denna agent representerar fraktprocessen och ansvarar för att skicka produkten tillbaka till säljaren. Denna agent kan användas både för återbetalningsprocessen och för allmän frakt av en produkt vid ett köp till exempel.
- **Feedbackagent**: Denna agent representerar feedbackprocessen och ansvarar för att samla in feedback från kunden. Feedback kan ges när som helst och inte bara under återbetalningsprocessen.
- **Eskaleringsagent**: Denna agent representerar eskaleringsprocessen och ansvarar för att eskalera problem till en högre supportnivå. Du kan använda denna typ av agent för vilken process som helst där du behöver eskalera ett problem.
- **Notifieringsagent**: Denna agent representerar notifieringsprocessen och ansvarar för att skicka notifieringar till kunden vid olika steg i återbetalningsprocessen.
- **Analysagent**: Denna agent representerar analysprocessen och ansvarar för att analysera data relaterad till återbetalningsprocessen.
- **Revisionagent**: Denna agent representerar revisionsprocessen och ansvarar för att granska återbetalningsprocessen för att säkerställa att den genomförs korrekt.
- **Rapporteringsagent**: Denna agent representerar rapporteringsprocessen och ansvarar för att generera rapporter om återbetalningsprocessen.
- **Kunskapsagent**: Denna agent representerar kunskapsprocessen och ansvarar för att underhålla en kunskapsbas med information relaterad till återbetalningsprocessen. Denna agent kan vara kunnig både inom återbetalningar och andra delar av din verksamhet.
- **Säkerhetsagent**: Denna agent representerar säkerhetsprocessen och ansvarar för att säkerställa säkerheten i återbetalningsprocessen.
- **Kvalitetsagent**: Denna agent representerar kvalitetsprocessen och ansvarar för att säkerställa kvaliteten i återbetalningsprocessen.

Det finns ganska många agenter listade ovan, både för den specifika återbetalningsprocessen men också för generella agenter som kan användas i andra delar av din verksamhet. Förhoppningsvis ger detta dig en idé om hur du kan bestämma vilka agenter du ska använda i ditt multi-agent system.

## Uppgift

Designa ett multi-agent system för en kundsupportprocess. Identifiera agenterna som är involverade i processen, deras roller och ansvar, och hur de interagerar med varandra. Överväg både agenter specifika för kundsupportprocessen och generella agenter som kan användas i andra delar av din verksamhet.
> Tänk efter innan du läser följande lösning, du kan behöva fler agenter än du tror.

> TIP: Tänk på de olika stadierna i kundsupportprocessen och överväg också agenter som behövs för något system.

## Solution

[Solution](./solution/solution.md)

## Knowledge checks

Question: När bör du överväga att använda multi-agenter?

- [ ] A1: När du har en liten arbetsbelastning och en enkel uppgift.
- [ ] A2: När du har en stor arbetsbelastning
- [ ] A3: När du har en enkel uppgift.

[Solution quiz](./solution/solution-quiz.md)

## Summary

I denna lektion har vi tittat på multi-agent designmönstret, inklusive de scenarier där multi-agenter är tillämpliga, fördelarna med att använda multi-agenter jämfört med en enskild agent, byggstenarna för att implementera multi-agent designmönstret, och hur man får insyn i hur de flera agenterna interagerar med varandra.

### Fler frågor om Multi-Agent designmönstret?

Gå med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) för att träffa andra elever, delta i öppna kontorstider och få dina frågor om AI-agenter besvarade.

## Additional resources

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">AutoGen design patterns</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentic design patterns</a>


## Previous Lesson

[Planning Design](../07-planning-design/README.md)

## Next Lesson

[Metacognition in AI Agents](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfriskrivning**:
Detta dokument har översatts med hjälp av AI-översättningstjänsten [Co-op Translator](https://github.com/Azure/co-op-translator). Även om vi strävar efter noggrannhet bör du vara medveten om att automatiska översättningar kan innehålla fel eller brister. Det ursprungliga dokumentet på dess modersmål bör betraktas som den auktoritativa källan. För kritisk information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för några missförstånd eller feltolkningar som uppstår till följd av användningen av denna översättning.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->