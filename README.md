[ai_receptionist_html.html](https://github.com/user-attachments/files/23845299/ai_receptionist_html.html)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aiderity Solutions - AI Receptionist Intake Form</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background: linear-gradient(135deg, #e0f2fe 0%, #ddd6fe 50%, #fae8ff 100%);
            min-height: 100vh;
            padding: 2rem 1rem;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
        }

        .form-card {
            background: white;
            border-radius: 1.5rem;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #0f172a 0%, #1e3a8a 50%, #000000 100%);
            padding: 3rem 2rem;
            text-align: center;
        }

        .logo-container {
            max-width: 300px;
            margin: 0 auto 1.5rem;
        }

        .logo-fallback {
            margin-bottom: 1.5rem;
        }

        .logo-fallback h1 {
            font-size: 3rem;
            font-weight: bold;
            background: linear-gradient(90deg, #22d3ee, #3b82f6, #eab308);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 0.5rem;
        }

        .logo-fallback .subtitle {
            font-size: 1.5rem;
            color: #cbd5e1;
            letter-spacing: 0.3em;
            font-weight: 300;
        }

        .header-text {
            color: #93c5fd;
            font-size: 1.25rem;
            margin-bottom: 0.5rem;
        }

        .header-subtext {
            color: #9ca3af;
            font-size: 0.875rem;
        }

        .form-content {
            padding: 3rem 2rem;
        }

        .section {
            margin-bottom: 3rem;
            padding-left: 1.5rem;
        }

        .section-border-indigo { border-left: 4px solid #6366f1; }
        .section-border-purple { border-left: 4px solid #a855f7; }
        .section-border-blue { border-left: 4px solid #3b82f6; }
        .section-border-green { border-left: 4px solid #10b981; }
        .section-border-orange { border-left: 4px solid #f97316; }
        .section-border-pink { border-left: 4px solid #ec4899; }

        .section-header {
            display: flex;
            align-items: center;
            margin-bottom: 2rem;
        }

        .section-icon {
            width: 1.5rem;
            height: 1.5rem;
            margin-right: 1rem;
        }

        .section-title {
            font-size: 1.5rem;
            font-weight: bold;
            color: #1f2937;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        label {
            display: block;
            font-size: 0.875rem;
            font-weight: 600;
            color: #374151;
            margin-bottom: 0.5rem;
        }

        .required {
            color: #ef4444;
        }

        input[type="text"],
        input[type="url"],
        textarea {
            width: 100%;
            padding: 0.75rem 1rem;
            border: 2px solid #d1d5db;
            border-radius: 0.5rem;
            font-size: 1rem;
            transition: border-color 0.2s;
        }

        input[type="text"]:focus,
        input[type="url"]:focus,
        textarea:focus {
            outline: none;
            border-color: #6366f1;
        }

        textarea {
            resize: vertical;
        }

        .radio-group,
        .checkbox-group {
            display: flex;
            flex-direction: column;
            gap: 0.75rem;
        }

        .radio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 0.75rem;
        }

        .radio-option,
        .checkbox-option {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            cursor: pointer;
        }

        input[type="radio"],
        input[type="checkbox"] {
            width: 1rem;
            height: 1rem;
            cursor: pointer;
        }

        .conditional-field {
            margin-top: 1rem;
            padding-left: 1.5rem;
        }

        .submit-btn {
            width: 100%;
            background: linear-gradient(90deg, #6366f1, #a855f7);
            color: white;
            padding: 1rem 1.5rem;
            border: none;
            border-radius: 0.75rem;
            font-size: 1.125rem;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s, box-shadow 0.2s;
            box-shadow: 0 10px 15px -3px rgba(99, 102, 241, 0.3);
            margin-top: 2rem;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 20px 25px -5px rgba(99, 102, 241, 0.4);
        }

        .submit-btn:active {
            transform: translateY(0);
        }

        .success-message {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            padding: 3rem;
            border-radius: 1.5rem;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            text-align: center;
            z-index: 1000;
            max-width: 500px;
            width: 90%;
        }

        .success-message.show {
            display: block;
        }

        .overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0.5);
            z-index: 999;
        }

        .overlay.show {
            display: block;
        }

        .checkmark {
            width: 5rem;
            height: 5rem;
            background: #10b981;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 1.5rem;
        }

        .checkmark svg {
            width: 3rem;
            height: 3rem;
            stroke: white;
        }

        .success-title {
            font-size: 2rem;
            font-weight: bold;
            color: #1f2937;
            margin-bottom: 1rem;
        }

        .success-text {
            color: #6b7280;
            margin-bottom: 2rem;
        }

        .close-btn {
            background: #6366f1;
            color: white;
            padding: 0.75rem 2rem;
            border: none;
            border-radius: 0.5rem;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.2s;
        }

        .close-btn:hover {
            background: #4f46e5;
        }

        .footer {
            text-align: center;
            margin-top: 2rem;
            color: #6b7280;
            font-size: 0.875rem;
        }

        .loading {
            display: none;
            margin-left: 0.5rem;
        }

        .loading.show {
            display: inline-block;
            width: 1rem;
            height: 1rem;
            border: 2px solid white;
            border-top-color: transparent;
            border-radius: 50%;
            animation: spin 0.6s linear infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        @media (max-width: 768px) {
            body {
                padding: 1rem;
            }

            .header {
                padding: 2rem 1rem;
            }

            .logo-fallback h1 {
                font-size: 2rem;
            }

            .logo-fallback .subtitle {
                font-size: 1rem;
            }

            .form-content {
                padding: 2rem 1rem;
            }

            .section {
                padding-left: 1rem;
            }

            .radio-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="overlay" id="overlay"></div>
    
    <div class="success-message" id="successMessage">
        <div class="checkmark">
            <svg fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7" />
            </svg>
        </div>
        <h2 class="success-title">Thank You!</h2>
        <p class="success-text">Your AI Receptionist intake form has been submitted successfully. We'll review your information and get back to you shortly.</p>
        <button class="close-btn" onclick="closeSuccess()">Close</button>
    </div>

    <div class="container">
        <div class="form-card">
            <div class="header">
                <div class="logo-fallback">
                    <h1>Aiderity</h1>
                    <p class="subtitle">SOLUTIONS</p>
                </div>
                <p class="header-text">AI Receptionist Intake Form</p>
                <p class="header-subtext">Help us build your perfect AI receptionist</p>
            </div>

            <div class="form-content">
                <form id="intakeForm">
                    <!-- Section 1: Business Information -->
                    <div class="section section-border-indigo">
                        <div class="section-header">
                            <svg class="section-icon" fill="none" stroke="#6366f1" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                            </svg>
                            <h2 class="section-title">Business Information</h2>
                        </div>

                        <div class="form-group">
                            <label>Business Name <span class="required">*</span></label>
                            <input type="text" name="businessName" required>
                        </div>

                        <div class="form-group">
                            <label>Industry <span class="required">*</span></label>
                            <div class="radio-grid">
                                <label class="radio-option">
                                    <input type="radio" name="industry" value="Salon" required>
                                    <span>Salon</span>
                                </label>
                                <label class="radio-option">
                                    <input type="radio" name="industry" value="Med Spa">
                                    <span>Med Spa</span>
                                </label>
                                <label class="radio-option">
                                    <input type="radio" name="industry" value="Real Estate">
                                    <span>Real Estate</span>
                                </label>
                                <label class="radio-option">
                                    <input type="radio" name="industry" value="Contractor / Home Services">
                                    <span>Contractor / Home Services</span>
                                </label>
                                <label class="radio-option">
                                    <input type="radio" name="industry" value="Coaching">
                                    <span>Coaching</span>
                                </label>
                                <label class="radio-option">
                                    <input type="radio" name="industry" value="Auto Services">
                                    <span>Auto Services</span>
                                </label>
                            </div>
                            <label class="radio-option" style="margin-top: 0.75rem;">
                                <input type="radio" name="industry" value="Other" id="industryOther">
                                <span>Other:</span>
                            </label>
                            <div id="industryOtherField" class="conditional-field" style="display: none;">
                                <input type="text" name="industryOtherText" placeholder="Specify your industry">
                            </div>
                        </div>

                        <div class="form-group">
                            <label>Describe your business in one sentence <span class="required">*</span></label>
                            <textarea name="businessDescription" rows="2" required></textarea>
                        </div>
                    </div>

                    <!-- Section 2: Services You Offer -->
                    <div class="section section-border-purple">
                        <div class="section-header">
                            <svg class="section-icon" fill="none" stroke="#a855f7" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z" />
                            </svg>
                            <h2 class="section-title">Services You Offer</h2>
                        </div>

                        <div class="form-group">
                            <label>List your services <span class="required">*</span></label>
                            <textarea name="services" rows="3" placeholder="e.g., Haircut, Color, Extensions, Blowout" required></textarea>
                        </div>

                        <div class="form-group">
                            <label>Pricing or price ranges</label>
                            <textarea name="pricing" rows="3" placeholder="e.g., Haircut: $50-75, Color: $100-200"></textarea>
                        </div>

                        <div class="form-group">
                            <label>Do you offer packages?</label>
                            <div class="radio-group">
                                <label class="radio-option">
                                    <input type="radio" name="hasPackages" value="Yes" id="packagesYes">
                                    <span>Yes</span>
                                </label>
                                <label class="radio-option">
                                    <input type="radio" name="hasPackages" value="No">
                                    <span>No</span>
                                </label>
                            </div>
                            <div id="packagesField" class="conditional-field" style="display: none;">
                                <textarea name="packages" rows="2" placeholder="Describe your packages"></textarea>
                            </div>
                        </div>
                    </div>

                    <!-- Section 3: Booking System -->
                    <div class="section section-border-blue">
                        <div class="section-header">
                            <svg class="section-icon" fill="none" stroke="#3b82f6" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
                            </svg>
                            <h2 class="section-title">Booking System</h2>
                        </div>

                        <div class="form-group">
                            <label>Scheduling link (Calendly / Acuity / GHL)</label>
                            <input type="url" name="schedulingLink" placeholder="https://calendly.com/your-link">
                        </div>

                        <div class="form-group">
                            <label>Appointment types you want the AI to book</label>
                            <textarea name="appointmentTypes" rows="3" placeholder="e.g., Consultation (30 min), Service Appointment (60 min)"></textarea>
                        </div>

                        <div class="form-group">
                            <label>Business hours</label>
                            <textarea name="businessHours" rows="2" placeholder="e.g., Mon-Fri: 9am-6pm, Sat: 10am-4pm, Sun: Closed"></textarea>
                        </div>
                    </div>

                    <!-- Section 4: FAQs & Knowledge Base -->
                    <div class="section section-border-green">
                        <div class="section-header">
                            <svg class="section-icon" fill="none" stroke="#10b981" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z" />
                            </svg>
                            <h2 class="section-title">FAQs & Knowledge Base</h2>
                        </div>

                        <div class="form-group">
                            <label>What common customer questions should the AI answer?</label>
                            <textarea name="commonQuestions" rows="4" placeholder="e.g., Do you accept walk-ins? What's your cancellation policy?"></textarea>
                        </div>

                        <div class="form-group">
                            <label>Provide answers to these questions</label>
                            <textarea name="faqAnswers" rows="4" placeholder="Provide detailed answers matching the questions above"></textarea>
                        </div>

                        <div class="form-group">
                            <label>Policies (cancellations, deposits, etc.)</label>
                            <textarea name="policies" rows="3" placeholder="e.g., 24-hour cancellation policy, 50% deposit required for first visit"></textarea>
                        </div>
                    </div>

                    <!-- Section 5: Lead Handling -->
                    <div class="section section-border-orange">
                        <div class="section-header">
                            <svg class="section-icon" fill="none" stroke="#f97316" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8" />
                            </svg>
                            <h2 class="section-title">Lead Handling</h2>
                        </div>

                        <div class="form-group">
                            <label>Where should new leads be sent? (Select all that apply)</label>
                            <div class="checkbox-group">
                                <label class="checkbox-option">
                                    <input type="checkbox" name="leadDestination" value="Email">
                                    <span>Email</span>
                                </label>
                                <label class="checkbox-option">
                                    <input type="checkbox" name="leadDestination" value="SMS">
                                    <span>SMS</span>
                                </label>
                                <label class="checkbox-option">
                                    <input type="checkbox" name="leadDestination" value="CRM" id="crmCheck">
                                    <span>CRM</span>
                                </label>
                            </div>
                            <div id="crmField" class="conditional-field" style="display: none;">
                                <input type="text" name="crmDetails" placeholder="Specify CRM (e.g., HubSpot, Salesforce)">
                            </div>
                        </div>

                        <div class="form-group">
                            <label>Preferred follow-up actions</label>
                            <textarea name="followUpActions" rows="3" placeholder="e.g., Send welcome email, Schedule follow-up call in 24 hours"></textarea>
                        </div>
                    </div>

                    <!-- Section 6: Tone & Personality -->
                    <div class="section section-border-pink">
                        <div class="section-header">
                            <svg class="section-icon" fill="none" stroke="#ec4899" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z" />
                            </svg>
                            <h2 class="section-title">Tone & Personality</h2>
                        </div>

                        <div class="form-group">
                            <label>Select a tone for your AI receptionist</label>
                            <div class="radio-group">
                                <label class="radio-option">
                                    <input type="radio" name="tone" value="Professional">
                                    <span>Professional</span>
                                </label>
                                <label class="radio-option">
                                    <input type="radio" name="tone" value="Friendly">
                                    <span>Friendly</span>
                                </label>
                                <label class="radio-option">
                                    <input type="radio" name="tone" value="High-end / Luxury">
                                    <span>High-end / Luxury</span>
                                </label>
                                <label class="radio-option">
                                    <input type="radio" name="tone" value="Energetic">
                                    <span>Energetic</span>
                                </label>
                                <label class="radio-option">
                                    <input type="radio" name="tone" value="Calm & Warm">
                                    <span>Calm & Warm</span>
                                </label>
                            </div>
                        </div>

                        <div class="form-group">
                            <label>Do you want a custom voice style?</label>
                            <textarea name="customVoice" rows="2" placeholder="Describe any specific voice characteristics you'd like"></textarea>
                        </div>
                    </div>

                    <!-- Section 7: Upload Files & Links -->
                    <div class="section section-border-indigo">
                        <div class="section-header">
                            <svg class="section-icon" fill="none" stroke="#6366f1" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12" />
                            </svg>
                            <h2 class="section-title">Upload Files & Links</h2>
                        </div>

                        <div class="form-group">
                            <label>Website URL</label>
                            <input type="url" name="websiteUrl" placeholder="https://yourbusiness.com">
                        </div>

                        <div class="form-group">
                            <label>Service menu (link or description)</label>
                            <input type="text" name="serviceMenu" placeholder="Link to your service menu or upload location">
                        </div>

                        <div class="form-group">
                            <label>Pricing sheet (link or description)</label>
                            <input type="text" name="pricingSheet" placeholder="Link to your pricing sheet or upload location">
                        </div>

                        <div class="form-group">
                            <label>Brand guidelines (link or description)</label>
                            <input type="text" name="brandGuidelines" placeholder="Link to your brand guidelines or upload location">
                        </div>

                        <div class="form-group">
                            <label>Previous call scripts (link or description)</label>
                            <input type="text" name="callScripts" placeholder="Link to your call scripts or upload location">
                        </div>
                    </div>

                    <button type="submit" class="submit-btn">
                        Submit Intake Form
                        <span class="loading" id="loading"></span>
                    </button>
                </form>
            </div>
        </div>

        <div class="footer">
            <p>© 2024 Aiderity Solutions. All rights reserved.</p>
        </div>
    </div>

    <script>
        // Handle conditional fields
        document.getElementById('industryOther').addEventListener('change', function() {
            document.getElementById('industryOtherField').style.display = this.checked ? 'block' : 'none';
        });

        document.getElementById('packagesYes').addEventListener('change', function() {
            document.getElementById('packagesField').style.display = this.checked ? 'block' : 'none';
        });

        document.getElementById('crmCheck').addEventListener('change', function() {
            document.getElementById('crmField').style.display = this.checked ? 'block' : 'none';
        });

        // Handle form submission
        document.getElementById('intakeForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            const form = e.target;
            const formData = new FormData(form);
            const loading = document.getElementById('loading');
            const submitBtn = form.querySelector('.submit-btn');
            
            // Get all checkbox values
            const leadDestinations = [];
            document.querySelectorAll('input[name="leadDestination"]:checked').forEach(checkbox => {
                leadDestinations.push(checkbox.value);
            });
            
            // Prepare data object
            const data = {
                _subject: `New AI Receptionist Intake - ${formData.get('businessName')}`,
                _template: 'table',
                'Business Name': formData.get('businessName'),
                'Industry': formData.get('industry') === 'Other' ? formData.get('industryOtherText') : formData.get('industry'),
                'Business Description': formData.get('businessDescription'),
                'Services': formData.get('services'),
                'Pricing': formData.get('pricing'),
                'Has Packages': formData.get('hasPackages'),
                'Packages': formData.get('packages'),
                'Scheduling Link': formData.get('schedulingLink'),
                'Appointment Types': formData.get('appointmentTypes'),
                'Business Hours': formData.get('businessHours'),
                'Common Questions': formData.get('commonQuestions'),
                'FAQ Answers': formData.get('faqAnswers'),
                'Policies': formData.get('policies'),
                'Lead Destination': leadDestinations.join(', '),
                'CRM Details': formData.get('crmDetails'),
                'Follow-up Actions': formData.get('followUpActions'),
                'Tone': formData.get('tone'),
                'Custom Voice': formData.get('customVoice'),
                'Website URL': formData.get('websiteUrl'),
                'Service Menu': formData.get('serviceMenu'),
                'Pricing Sheet': formData.get('pricingSheet'),
                'Brand Guidelines': formData.get('brandGuidelines'),
                'Call Scripts': formData.get('callScripts'),
                'Submission Date': new Date().toLocaleString()
            };
            
            // Show loading
            loading.classList.add('show');
            submitBtn.disabled = true;
            
            try {
                const response = await fetch('https://formsubmit.co/ajax/aiderityinfo@gmail.com', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Accept': 'application/json'
                    },
                    body: JSON.stringify(data)
                });
                
                if (response.ok) {
                    document.getElementById('overlay').classList.add('show');
                    document.getElementById('successMessage').classList.add('show');
                    form.reset();
                } else {
                    alert('There was an error submitting the form. Please try again or email us directly at aiderityinfo@gmail.com');
                }
            } catch (error) {
                console.error('Error:', error);
                alert('There was an error submitting the form. Please try again or email us directly at aiderityinfo@gmail.com');
            } finally {
                loading.classList.remove('show');
                submitBtn.disabled = false;
            }
        });

        function closeSuccess() {
            document.getElementById('overlay').classList.remove('show');
            document.getElementById('successMessage').classList.remove('show');
        }

        // Close on overlay click
        document.getElementById('overlay').addEventListener('click', closeSuccess);
    </script>
</body>
</html>
