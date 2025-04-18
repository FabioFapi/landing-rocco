<script>
    import { onMount } from 'svelte';
    import { fade, fly } from 'svelte/transition';
    
    let visible = false;
    
    onMount(() => {
      // Attiva le animazioni dopo il caricamento
      setTimeout(() => {
        visible = true;
      }, 300);
    });
  </script>
  
  <section class="flex w-full justify-center px-6 py-8 invitation-container">
      {#if visible}
          <div class="max-w-[360px] text-center text-black space-y-6 invitation-content" in:fade={{ duration: 800 }}>
  
              <p class="greeting" in:fly={{ y: 20, duration: 600, delay: 100 }}>Dear Friends and Family,</p>
  
              <p class="text-base leading-relaxed paragraph" in:fly={{ y: 20, duration: 600, delay: 300 }}>
                  I am delighted to invite you to join me in<br />
                  celebrating a special milestone — my birthday.
              </p>
  
              <p class="text-base leading-relaxed paragraph" in:fly={{ y: 20, duration: 600, delay: 500 }}>
                  It would mean a lot to have you there as I mark<br />
                  another year of life, growth, and gratitude.
              </p>
  
              <p class="text-base leading-relaxed paragraph" in:fly={{ y: 20, duration: 600, delay: 700 }}>
                  Your presence would truly make the day memorable,and<br />
                  I would be honored to celebrate this occasion<br />
                  with those closest to me.
              </p>
  
              <p class="text-base leading-relaxed paragraph" in:fly={{ y: 20, duration: 600, delay: 900 }}>
                  I truly look forward to celebrating together and<br />
                  sharing this joyful day with you.
              </p>
  
              <p class="mt-6 signature" in:fly={{ y: 20, duration: 600, delay: 1100 }}>
                  Warm regards,<br />
                  Rocco
              </p>
  
          </div>
      {/if}
  </section>
  
  <style>
    .invitation-container {
      perspective: 1000px;
    }
    
    .invitation-content {
      position: relative;
      transform-style: preserve-3d;
      animation: float 6s ease-in-out infinite;
    }
    
    .greeting, .signature {
      position: relative;
      transition: transform 0.3s ease, color 0.3s ease;
    }
    
    .greeting:hover, .signature:hover {
      transform: scale(1.05);
      color: #9c4e4e;
    }
    
    .paragraph {
      position: relative;
      transition: transform 0.3s ease, text-shadow 0.3s ease;
      animation: breathe 4s infinite ease-in-out;
    }
    
    .paragraph:hover {
      transform: translateY(-3px);
      text-shadow: 1px 1px 3px rgba(0,0,0,0.1);
    }
    
    @keyframes float {
      0% {
        transform: translateY(0px);
        box-shadow: 0 5px 15px rgba(0,0,0,0.05);
      }
      50% {
        transform: translateY(-10px);
        box-shadow: 0 15px 25px rgba(0,0,0,0.08);
      }
      100% {
        transform: translateY(0px);
        box-shadow: 0 5px 15px rgba(0,0,0,0.05);
      }
    }
    
    @keyframes breathe {
      0%, 100% {
        opacity: 1;
      }
      50% {
        opacity: 0.95;
      }
    }
    
    /* Decorative pen marks that appear drawn-in on hover */
    .invitation-content::before {
      content: "";
      position: absolute;
      top: -20px;
      left: -30px;
      width: calc(100% + 60px);
      height: calc(100% + 40px);
      border: 2px solid transparent;
      border-radius: 10px;
      transition: border-color 0.6s ease;
      z-index: -1;
      pointer-events: none;
    }
    
    .invitation-content:hover::before {
      border-color: rgba(156, 78, 78, 0.2);
    }
  </style>