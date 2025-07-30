<script lang="ts">
  import { Button } from "$lib/components/ui/button"; 
  import { Card, CardContent, CardDescription, CardHeader, CardTitle } from "$lib/components/ui/card";
  import { Input } from "$lib/components/ui/input"; 
  import DonationCard from "$lib/components/donation-card.svelte"; 
  import ImpactMetric from "$lib/components/impact-metric.svelte"; 
  import TestimonialCard from "$lib/components/testimonial-card.svelte";
  import ProgressBar from "$lib/components/progress-bar.svelte";

  // Import Lucide Svelte icons
  import {
    Heart,
    Users,
    GraduationCap,
    Code,
    Globe,
    Target,
    Award,
    TrendingUp,
    Coffee,
    Laptop,
    BookOpen,
    Github,
    Youtube,
    Mail,
    MapPin,
  } from "@lucide/svelte"; // Assuming lucide-svelte is installed

  // Image imports (adjust paths based on your Svelte project structure)
  import heroImage from "$lib/assets/hero-training.jpg";
  import impactImage from "$lib/assets/impact-learning.jpg";
  import successImage from "$lib/assets/success-story.jpg";

  let customAmount: string = "";

  const handleDonation = (amount: string) => {
    // In a real app, this would integrate with Stripe or another payment processor
    console.log(`Initiating donation of ${amount}`);
    // For now, show an alert
    alert(`Thank you for your interest in donating ${amount}! Payment integration would be implemented here.`);
  };

  const handleCustomDonation = () => {
    if (customAmount && parseFloat(customAmount) > 0) {
      handleDonation(`$${customAmount}`);
    }
  };

  $: isCustomAmountValid = customAmount && parseFloat(customAmount) > 0;
</script>

<div class="min-h-screen bg-background">
  <nav class="border-b border-border bg-background/95 backdrop-blur supports-[backdrop-filter]:bg-background/60 sticky top-0 z-50">
    <div class="container mx-auto px-4 py-4 flex justify-between items-center">
      <div class="flex items-center gap-2">
        <div class="w-8 h-8 bg-gradient-primary rounded-lg"></div>
        <span class="text-xl font-bold">Living Open Source Foundation</span>
      </div>
      <div class="hidden md:flex items-center gap-6">
        <a href="#impact" class="text-muted-foreground hover:text-primary transition-colors">Impact</a>
        <a href="#donate" class="text-muted-foreground hover:text-primary transition-colors">Donate</a>
        <a href="#stories" class="text-muted-foreground hover:text-primary transition-colors">Stories</a>
        <Button variant="default" size="sm">Donate Now</Button>
      </div>
    </div>
  </nav>

  <section class="relative py-20 lg:py-32 overflow-hidden">
    <div class="absolute inset-0 bg-gradient-hero opacity-90"></div>
    <div class="absolute inset-0">
      <img
        src={heroImage}
        alt="African students learning open source technologies"
        class="w-full h-full object-cover"
      />
    </div>
    <div class="relative container mx-auto px-4 text-center text-white">
      <h1 class="text-4xl md:text-6xl font-bold mb-6 animate-fade-in">
        Empowering Africa Through
        <span class="block bg-gradient-to-r from-orange-300 to-red-300 bg-clip-text text-transparent">
          Open Source Technology
        </span>
      </h1>
      <p class="text-xl md:text-2xl mb-8 max-w-3xl mx-auto opacity-90 animate-fade-in">
        We train African communities in Linux, Docker, and Kubernetes, equipping them with the skills
        for emerging technologies and creating opportunities for economic growth.
      </p>
      <div class="flex flex-col sm:flex-row gap-4 justify-center animate-scale-in">
        <Button variant="default" size="lg" class="text-lg px-8 py-6">
          <Heart class="w-5 h-5 mr-2" />
          Start Your Impact
        </Button>
        <Button variant="outline" size="lg" class="text-lg px-8 py-6 bg-white/10 border-white/30 text-white hover:bg-white/20">
          <BookOpen class="w-5 h-5 mr-2" />
          Learn Our Mission
        </Button>
      </div>
    </div>
  </section>

  <section id="impact" class="py-20 bg-gradient-subtle">
    <div class="container mx-auto px-4">
      <div class="text-center mb-16">
        <h2 class="text-3xl md:text-4xl font-bold mb-4">Our Growing Impact</h2>
        <p class="text-xl text-muted-foreground max-w-2xl mx-auto">
          Since our founding, we've been transforming lives across Africa through technology education
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 mb-16">
        <ImpactMetric
          number="2,847"
          label="Students Trained"
          description="Individuals equipped with Linux, Docker & Kubernetes skills"
        />
        <ImpactMetric
          number="67%"
          label="Job Placement Rate"
          description="Graduates securing tech positions within 6 months"
        />
        <ImpactMetric
          number="15"
          label="African Countries"
          description="Nations where our programs are making a difference"
        />
        <ImpactMetric
          number="$47K"
          label="Average Salary Increase"
          description="Income boost for our program graduates"
        />
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
        <div>
          <h3 class="text-2xl font-bold mb-6">Transforming Communities</h3>
          <div class="space-y-4">
            <div class="flex items-center gap-3">
              <Code class="w-6 h-6 text-primary" />
              <span>Linux System Administration Training</span>
            </div>
            <div class="flex items-center gap-3">
              <Laptop class="w-6 h-6 text-primary" />
              <span>Docker Containerization Workshops</span>
            </div>
            <div class="flex items-center gap-3">
              <Globe class="w-6 h-6 text-primary" />
              <span>Kubernetes Orchestration Certification</span>
            </div>
            <div class="flex items-center gap-3">
              <Users class="w-6 h-6 text-primary" />
              <span>Community-Led Learning Groups</span>
            </div>
          </div>
        </div>
        <div class="relative">
          <img
            src={impactImage}
            alt="Students learning together"
            class="rounded-lg shadow-elegant w-full h-80 object-cover"
          />
          <div class="absolute inset-0 bg-gradient-primary opacity-10 rounded-lg"></div>
        </div>
      </div>
    </div>
  </section>

  <section class="py-20">
    <div class="container mx-auto px-4">
      <div class="bg-white rounded-2xl shadow-elegant p-8 lg:p-12 border border-border">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
          <div>
            <h2 class="text-3xl font-bold mb-4 text-primary">
              <Target class="w-8 h-8 inline mr-3" />
              Current Campaign: Ubuntu Server Labs
            </h2>
            <p class="text-lg text-muted-foreground mb-6">
              Help us establish 10 new Ubuntu Server training labs across Ghana, Nigeria, and Kenya.
              Each lab will serve 200+ students annually with hands-on Linux administration experience.
            </p>
            <ProgressBar
              current={47300}
              goal={85000}
              label="Ubuntu Server Labs Fundraising Goal"
            />
          </div>
          <div class="space-y-4">
            <h3 class="text-xl font-semibold mb-4">What Your Donation Provides:</h3>
            <div class="space-y-3">
              <div class="flex items-center gap-3 p-3 rounded-lg bg-gradient-subtle">
                <Coffee class="w-5 h-5 text-primary" />
                <span>$25 - Daily training materials for 5 students</span>
              </div>
              <div class="flex items-center gap-3 p-3 rounded-lg bg-gradient-subtle">
                <Laptop class="w-5 h-5 text-primary" />
                <span>$100 - Server hardware for hands-on practice</span>
              </div>
              <div class="flex items-center gap-3 p-3 rounded-lg bg-gradient-subtle">
                <Award class="w-5 h-5 text-primary" />
                <span>$500 - Complete lab setup for one training center</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section id="donate" class="py-20 bg-gradient-subtle">
    <div class="container mx-auto px-4">
      <div class="text-center mb-16">
        <h2 class="text-3xl md:text-4xl font-bold mb-4">Choose Your Impact Level</h2>
        <p class="text-xl text-muted-foreground max-w-2xl mx-auto">
          Every contribution makes a difference. Select the giving level that works for you.
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 mb-12">
        <DonationCard
          title="Supporter"
          amount="$25"
          description="Essential training support"
          features={[
            "Training materials for 5 students",
            "Ubuntu installation guides",
            "Basic Docker tutorials",
            "Community forum access"
          ]}
          onClick={() => handleDonation("$25")}
        />

        <DonationCard
          title="Advocate"
          amount="$100"
          description="Enhanced learning experience"
          features={[
            "Server hardware for labs",
            "Advanced Kubernetes workshops",
            "Certification preparation",
            "Mentorship program access",
            "Monthly progress reports"
          ]}
          onClick={() => handleDonation("$100")}
        />

        <DonationCard
          title="Champion"
          amount="$500"
          description="Complete lab transformation"
          isPopular={true}
          features={[
            "Full lab setup for training center",
            "Instructor certification program",
            "6-month curriculum development",
            "Job placement assistance",
            "Recognition on donor wall",
            "Video updates from students"
          ]}
          onClick={() => handleDonation("$500")}
        />

        <DonationCard
          title="Visionary"
          amount="$1,000"
          description="Community-wide impact"
          features={[
            "Sponsor entire training cohort",
            "Advanced cloud infrastructure setup",
            "Scholarship fund contribution",
            "Annual impact visit opportunity",
            "Direct student communication",
            "Legacy program naming rights"
          ]}
          onClick={() => handleDonation("$1,000")}
        />
      </div>

      <Card class="max-w-md mx-auto shadow-elegant">
        <CardHeader class="text-center">
          <CardTitle>Custom Donation</CardTitle>
          <CardDescription>Choose your own impact amount</CardDescription>
        </CardHeader>
        <CardContent class="space-y-4">
          <div class="flex gap-2">
            <div class="flex-1">
              <Input
                type="number"
                placeholder="Enter amount"
                bind:value={customAmount}
                class="text-center text-lg"
              />
            </div>
          </div>
          <Button
            variant="default"
            size="lg"
            class="w-full"
            onclick={handleCustomDonation}
            disabled={!isCustomAmountValid}
          >
            Donate ${customAmount || "0"}
          </Button>
        </CardContent>
      </Card>
    </div>
  </section>

  <section id="stories" class="py-20">
    <div class="container mx-auto px-4">
      <div class="text-center mb-16">
        <h2 class="text-3xl md:text-4xl font-bold mb-4">Success Stories</h2>
        <p class="text-xl text-muted-foreground max-w-2xl mx-auto">
          Meet the graduates who are transforming their communities with open source technologies
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 mb-12">
        <TestimonialCard
          quote="The Linux training changed my life completely. I went from unemployed to landing a DevOps role at a major tech company in Lagos. The hands-on Docker experience was invaluable."
          name="Amara Okafor"
          title="DevOps Engineer"
          location="Lagos, Nigeria"
          image={successImage}
        />

        <TestimonialCard
          quote="Learning Kubernetes through this program opened doors I never imagined. I now lead cloud infrastructure for three startups and mentor other women in tech."
          name="Fatima Al-Rashid"
          title="Cloud Solutions Architect"
          location="Cairo, Egypt"
          image={successImage}
        />

        <TestimonialCard
          quote="From traditional farming to tech entrepreneurship - the foundation's training gave me the skills to build a platform connecting farmers with markets using containerized applications."
          name="Kwame Asante"
          title="Tech Entrepreneur"
          location="Accra, Ghana"
          image={successImage}
        />
      </div>

      <div class="text-center">
        <Button variant="outline" size="lg">
          <TrendingUp class="w-5 h-5 mr-2" />
          View More Success Stories
        </Button>
      </div>
    </div>
  </section>

  <footer class="bg-foreground text-background py-16">
    <div class="container mx-auto px-4">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 mb-8">
        <div>
          <div class="flex items-center gap-2 mb-4">
            <div class="w-8 h-8 bg-gradient-primary rounded-lg"></div>
            <span class="text-xl font-bold">Living Open Source Foundation</span>
          </div>
          <p class="text-background/80 mb-4">
            Empowering African communities through open source technology education and training.
          </p>
          <div class="flex gap-4">
            <Github class="w-5 h-5 text-background/60 hover:text-primary cursor-pointer transition-colors" />
            <Youtube class="w-5 h-5 text-background/60 hover:text-primary cursor-pointer transition-colors" />
            <Mail class="w-5 h-5 text-background/60 hover:text-primary cursor-pointer transition-colors" />
          </div>
        </div>

        <div>
          <h3 class="font-semibold mb-4">Programs</h3>
          <ul class="space-y-2 text-background/80">
            <li>Linux Administration</li>
            <li>Docker Containerization</li>
            <li>Kubernetes Orchestration</li>
            <li>Cloud Infrastructure</li>
          </ul>
        </div>

        <div>
          <h3 class="font-semibold mb-4">Get Involved</h3>
          <ul class="space-y-2 text-background/80">
            <li>Donate Now</li>
            <li>Volunteer</li>
            <li>Corporate Partnerships</li>
            <li>Sponsor a Student</li>
          </ul>
        </div>

        <div>
          <h3 class="font-semibold mb-4">Contact</h3>
          <div class="space-y-2 text-background/80">
            <div class="flex items-center gap-2">
              <Mail class="w-4 h-4" />
              <span>info@losf.org</span>
            </div>
            <div class="flex items-center gap-2">
              <MapPin class="w-4 h-4" />
              <span>Multiple locations across Africa</span>
            </div>
          </div>
        </div>
      </div>

      <div class="border-t border-background/20 pt-8 text-center text-background/60">
        <p>&copy; 2025 Living Open Source Foundation. All rights reserved.</p>
      </div>
    </div>
  </footer>
</div>