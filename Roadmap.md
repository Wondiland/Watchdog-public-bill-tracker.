# Watchdog Development Roadmap

This roadmap outlines the path from prototype to production-ready transparency platform. Each phase builds on the previous one, with clear milestones and deliverables.

---

## 📍 Current Status: Phase 0 (Prototype)

✅ **What's Done:**
- Working React frontend with sample data
- Detection logic for all four flag types (late-night, fast-track, text changes, holidays)
- Search and filter functionality
- User verification workflow
- Clean, documented codebase

🔨 **What's Missing:**
- Real government data feeds
- Backend infrastructure
- Database
- User accounts
- Notifications

---

## 🎯 Phase 1: Minimum Viable Product (4-6 weeks)

**Goal:** Get it working with real data for Federal parliament only.

### Milestone 1.1: Backend Foundation (Week 1-2)
- [ ] Set up PostgreSQL database
- [ ] Design and implement database schema (bills, flags, logs)
- [ ] Build REST API with FastAPI or Express
  - `GET /api/bills` — List bills with pagination
  - `GET /api/bills/:id` — Get bill details
  - `GET /api/flags` — Get flagged bills only
- [ ] Deploy database and API to DigitalOcean/AWS
- [ ] Add basic error logging

**Deliverable:** Working API that serves sample data

### Milestone 1.2: Federal Data Integration (Week 2-3)
- [ ] Research and document Federal Register API
- [ ] Build scraper for Parliament of Australia bills
- [ ] Build scraper for Hansard (voting records)
- [ ] Parse bill text and calculate change percentages
- [ ] Create scheduled job (runs every 30 min)
- [ ] Store scraped data in database
- [ ] Add data validation and error handling

**Deliverable:** Live data flowing into database automatically

### Milestone 1.3: Frontend Integration (Week 3-4)
- [ ] Connect React app to real API (remove sample data)
- [ ] Add loading states and error handling
- [ ] Implement proper timezone handling (Brisbane/Canberra)
- [ ] Add "Last updated" timestamp
- [ ] Optimize performance for larger datasets
- [ ] Deploy frontend to Vercel or similar

**Deliverable:** Public website showing real Federal bills

### Milestone 1.4: Email Notifications (Week 4-5)
- [ ] Set up SendGrid account
- [ ] Design email template for daily digest
- [ ] Build subscription form (email only, no accounts)
- [ ] Create email job (sends daily at 7am)
- [ ] Add unsubscribe functionality
- [ ] Test with beta group (20-50 people)

**Deliverable:** Daily email digest to subscribers

### Milestone 1.5: Testing & Launch (Week 5-6)
- [ ] Write unit tests for detection logic
- [ ] Write integration tests for API
- [ ] Test with various bill types and edge cases
- [ ] Create deployment documentation
- [ ] Set up monitoring (Sentry, Datadog, or similar)
- [ ] Public launch announcement

**Deliverable:** Production-ready MVP serving Federal data

**Estimated Cost:** AUD $8,000–$15,000 (if paying developers) or volunteer time
**Ongoing Cost:** ~AUD $50–$150/month (hosting, SendGrid)

---

## 🚀 Phase 2: Scale to All States (8-12 weeks)

**Goal:** Cover all Australian jurisdictions and add user accounts.

### Milestone 2.1: Queensland Integration (Week 1-2)
- [ ] Build scraper for QLD Parliament
- [ ] Add QLD-specific holidays to detection
- [ ] Update database schema for state variations
- [ ] Test with QLD historical data

### Milestone 2.2: Other States (Week 3-6)
- [ ] New South Wales
- [ ] Victoria
- [ ] South Australia
- [ ] Western Australia
- [ ] Tasmania
- [ ] Northern Territory
- [ ] Australian Capital Territory

*Note: Each state has different data formats and APIs. Budget 3-5 days per state.*

### Milestone 2.3: User Accounts (Week 7-9)
- [ ] Build authentication system (email/password or social login)
- [ ] Create user dashboard
- [ ] Add watchlist functionality (save specific bills)
- [ ] Add custom keyword alerts
- [ ] Add notification preferences (email frequency, jurisdictions)
- [ ] GDPR/privacy policy compliance

### Milestone 2.4: Mobile Optimization (Week 10-11)
- [ ] Responsive design improvements
- [ ] Progressive Web App (PWA) setup
- [ ] Push notifications (optional)
- [ ] Mobile-specific UI tweaks

### Milestone 2.5: Testing & Refinement (Week 11-12)
- [ ] Load testing (can it handle 10k users?)
- [ ] Bug fixes and polish
- [ ] User feedback implementation
- [ ] Documentation updates

**Estimated Cost:** AUD $20,000–$45,000 (if paying developers)
**Ongoing Cost:** ~AUD $150–$300/month (more data, more users)

---

## 📈 Phase 3: Advanced Features (6-12 months)

**Goal:** Become the definitive source for Australian legislative transparency.

### Feature 3.1: Historical Analysis
- [ ] Import historical bill data (past 5-10 years)
- [ ] Trend analysis dashboard
  - "Late-night votes are up 40% this year"
  - "This government rushes bills more than the previous one"
- [ ] Comparative metrics by jurisdiction
- [ ] Data visualization (charts, graphs)

### Feature 3.2: Community Features
- [ ] User comments on bills
- [ ] "Is this concerning?" voting system
- [ ] Verified expert annotations
- [ ] Share bill alerts on social media
- [ ] Discussion forums or Reddit integration

### Feature 3.3: Public API
- [ ] REST API for researchers and journalists
- [ ] API documentation
- [ ] Rate limiting and authentication
- [ ] CSV/JSON export functionality
- [ ] Webhooks for real-time alerts

### Feature 3.4: Mobile Apps
- [ ] Native iOS app
- [ ] Native Android app
- [ ] Push notifications
- [ ] Offline mode

### Feature 3.5: Advanced Detection
- [ ] Machine learning to detect similar bills
- [ ] Sentiment analysis of parliamentary debates
- [ ] Lobbying and donation correlation
- [ ] Bill complexity scoring
- [ ] "Who benefits?" analysis (which industries/groups)

### Feature 3.6: Media Integration
- [ ] Partnerships with news outlets
- [ ] Automated press releases for major flags
- [ ] Data journalism collaborations
- [ ] Public datasets for researchers

**Estimated Cost:** Varies by feature (AUD $50k–$200k+ total)
**Ongoing Cost:** ~AUD $300–$1,000/month (scaling infrastructure)

---

## 🌍 Phase 4: International Expansion (Long-term)

- [ ] New Zealand parliament
- [ ] UK parliament
- [ ] Canadian parliament
- [ ] US Congress (federal)
- [ ] US state legislatures
- [ ] EU institutions

*Note: Each country requires new data sources, legal research, and localization.*

---

## 📊 Success Metrics

**Phase 1 Success:**
- 1,000+ subscribers to email alerts
- 10+ bills flagged per month
- 5+ media mentions
- 3+ active contributors

**Phase 2 Success:**
- 10,000+ users
- All Australian jurisdictions covered
- 50+ bills flagged per month
- 10+ active contributors
- Partnership with 1+ major news outlet

**Phase 3 Success:**
- 50,000+ users
- API used by 5+ research institutions
- Proven impact (e.g., media coverage leading to bill amendments)
- Sustainable funding model

---

## 💰 Funding Strategy

### Short-term (Phase 1)
- Volunteer contributions
- Small personal investment (AUD $2k–$5k)
- Crowdfunding campaign?

### Medium-term (Phase 2-3)
- Grant applications:
  - Google.org grants
  - Mozilla Foundation
  - Knight Foundation
  - Local Australian civic tech grants
- Donations from users
- Sponsorships from transparency orgs

### Long-term (Phase 4)
- Subscription tier for premium features (API access, advanced analytics)
- Institutional partnerships
- Government contracts (ironic but possible)
- Foundation support

---

## 🎯 Next Actions (Right Now)

If you're reading this and want to contribute:

1. **Developers:** Check [CONTRIBUTING.md](CONTRIBUTING.md) and grab an issue
2. **Data people:** Help document government APIs
3. **Designers:** Improve the UI/UX
4. **Writers:** Help with documentation or blog posts
5. **Everyone:** Star the repo and share it

---

## 📅 Timeline Summary

| Phase | Duration | Key Outcome |
|-------|----------|-------------|
| **Phase 0** | Complete | Working prototype with sample data |
| **Phase 1** | 4-6 weeks | MVP with Federal data and email alerts |
| **Phase 2** | 8-12 weeks | All states + user accounts |
| **Phase 3** | 6-12 months | Advanced features and community |
| **Phase 4** | 1-3 years | International expansion |

---

## ⚠️ Risks & Challenges

**Technical:**
- Government APIs are often unreliable or poorly documented
- Data formats vary wildly between jurisdictions
- Parsing bill text accurately is hard (legal language is complex)
- Scaling to handle high traffic during major political events

**Political:**
- Potential pushback from governments (unlikely but possible)
- Accusations of bias (we must remain neutral)
- Legal challenges re: copyright on bill text (probably fine but worth checking)

**Sustainability:**
- Open source projects often lose momentum after initial excitement
- Ongoing maintenance costs money
- Burnout risk for core contributors

**Mitigation:**
- Start small (Federal only)
- Document everything obsessively
- Build a community, not a solo project
- Secure funding early
- Stay strictly non-partisan

---

## 📞 Questions or Ideas?

Open an issue or email akka@duck.com

**Let's build something that actually makes democracy more transparent.** 🔍
